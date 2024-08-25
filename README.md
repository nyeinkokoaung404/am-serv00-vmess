# [am-serv00-vmess](https://github.com/amclubs/am-serv00-vmess)
▶️ **Newcomer [YouTube](https://youtube.com/@AM_CLUB)** needs your support, please help me **like**, **follow**, **turn on the little bell**, ***thank you very much!!! *** ✅
</br>🎁 Don't just download or fork. Please **follow** my GitHub and give all my projects a **Star** star (please)! Your support is my motivation to keep moving forward! 💖
</br>✅**To unlock more technologies, please visit [【Personal Blog】](https://am.809098.xyz)**, join the TG group [【AM Technology | Sharing and Exchange Group】](https://t.me/AM_CLUBS)
#
# Disclaimer

### Purpose
This project is designed and developed for learning, research and security testing purposes only. It is intended to provide a tool for security researchers, academics and technology enthusiasts to understand and practice network communication technology.

### Legality
Users must comply with local laws and regulations when downloading and using this project. Users are responsible for ensuring that their actions comply with the laws, regulations and other applicable regulations in their region.

### Disclaimer
1. As the author of this project, I (hereinafter referred to as the "Author") emphasize that this project should be used only for legal, ethical and educational purposes.
2. The author does not encourage, support or promote any form of illegal use of this project. If it is found that this project is used for illegal or unethical activities, the author will strongly condemn such behavior.
3. The author is not responsible for any illegal activities carried out by any person or group using this project. Any consequences arising from the use of this project by the user shall be borne by the user himself.
4. The author is not responsible for any direct or indirect damages that may be caused by the use of this project.
5. By using this project, the user understands and agrees to all the terms of this disclaimer. If the user does not agree to these terms, he should stop using the project immediately.

The author reserves the right to update this disclaimer at any time without prior notice. The latest version of the disclaimer will be published on the project's GitHub page.

# Free serv00 server one-click script deployment VMess

The script of this project installs, manages and runs a VMess node, and can set up domain name back to the source through Cloudflare's CDN for acceleration, unlocking ChatGPT, TikTok, other streaming media, small websites, etc.

# Deployment tutorial:

## [Video tutorial](https://youtu.be/6UZXHfc3zEU)

## 1. Prerequisites to prepare
### 1. First, register a Serv00 account. It is recommended to register with a gmail email. After registration, there will be an email with your username and password when you registered.
- Registered account address: https://serv00.com
<center>Please see the video below to register an account</center>
<center><a href="https://youtu.be/NET1FTlfDTs">[Click to watch the video tutorial]</a></center>

![image](https://github.com/user-attachments/assets/57c3ff7b-ae42-42c0-87ac-acb1b5bd177a)

### 2. Add the group and send the keyword ssh to get the connection tool
Telegram channel: [@AM_CLUBS](https://t.me/AM_CLUBS)

## 2. Initial settings before installation
- 1. Log in to the email and send the URL behind your DevilWEB webpanel. After entering the website, click Change language to change the panel to English
- 2. Then click Additonal services in the left column, then click Run your own applications and see an Enable click
- 3. Find Port reservation and click Add Port behind it to open a new port. You can write anything you want, or click Random behind Port to randomly select a Port type and select TCP
- 4. Then click Port list and you will see a port
![image](https://github.com/user-attachments/assets/1b11ebdb-49e6-427d-a074-f51d52235f7e)


- 5. Enable administrative privileges:
<img width="800" height="600" alt="serv00" src="https://github.com/user-attachments/assets/48466f3a-1b75-4cf3-8dd9-7c2e440b73fe">

***After completing this step, exit SSH and log in again. ***

## 3. Start installation and deployment

- 1. Log in to SSH using the tool we downloaded earlier (some tools will still pop up a password for the first connection, remember to click X and then add the password)
Use serv00 to send you information via email (username and panel below should be changed to the corresponding information received in your email).
```
ssh <username>@<panel>.serv00.com
```

- 2. After entering the panel, copy the following code to install it with one click
```
bash <(curl -Ls https://raw.githubusercontent.com/amclubs/am-serv00-vmess/main/install_serv00_vmess.sh)
```

- 3. Keep alive command (sometimes after the hen restarts, all processes and scheduled tasks will be deleted, so you need to manually re-execute the following keep alive command to make the scheduled task effective. Don't ask why, because it is a free sequela)
```
(crontab -l; echo "*/12 * * * * pgrep -x "web" > /dev/null || nohup /home/${USER}/.vmess/web run -c /home/${USER}/.vmess/config.json >/dev/null 2>&1 &") | crontab -
```
### The tunnel keepalive command is as follows
- Default tunnel keepalive command, <your panel open port> needs to modify your port
```
(crontab -l; echo "*/12 * * * * pgrep -x "bot" > /dev/null || nohup /home/${USER}/.vmess/bot tunnel --edge-ip-version auto --no-autoupdate --protocol http2 --logfile /home/${USER}/.vmess/boot.log --loglevel info --url http://localhost:<your panel open port> >/dev/null 2>&1 &") | crontab -
```
- Token fixed tunnel keepalive command, <ARGO_AUTH> needs to modify your token
```
(crontab -l; echo "*/12 * * * * pgrep -x "bot" > /dev/null || nohup /home/${USER}/.vmess/bot tunnel --edge-ip-version auto --no-autoupdate --protocol http2 run --token <ARGO_AUTH> >/dev/null 2>&1 &") | crontab -
```
- json fixed tunnel keepalive command
```
(crontab -l; echo "*/12 * * * * pgrep -x "bot" > /dev/null || nohup /home/${USER}/.vmess/bot tunnel --edge-ip-version auto --config tunnel.yml run >/dev/null 2>&1 &") | crontab -
```
- View keepalive crontab tasks
```
crontab -l
```
- After the above command is completed, the following information will be displayed, indicating that the keepalive setting is successful
```
*/12 * * * * pgrep -x "web" > /dev/null || nohup /home/${USER}/.vmess/web run -c /home/${USER}/.vmess/config.json >/dev/null 2>&1 &
```

## 4. Test node
- 1. Copy the node information returned after successful installation to the subscription tool and you can use it

- 2. If you don’t remember the node configuration, you can check it through the following information
```
cat /home/${USER}/.vmess/list.txt
```
- 3. The node is accelerated by setting the domain name back to the source through Cloudflare’s CDN
- CF port type

HTTP：80，8080，8880，2052，2082，2086，2095

HTTPS：443，2053，2083，2087，2096，8443

- 4. Please check the video tutorial (Cloudflare's CDN settings domain name back to the source for acceleration) [Video tutorial](https://youtu.be/6UZXHfc3zEU)
- 5. [Free domain name registration tutorial](https://youtu.be/cI36vtXuQrM)

## 5. Uninstall VMess
### One-click uninstall command, according to the prompt, select 2 (2. Uninstall sing-box) Direct uninstallation completed
```
bash <(curl -Ls https://raw.githubusercontent.com/amclubs/am-serv00-vmess/main/install_serv00_vmess.sh)
```


