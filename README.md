# *N*panel-UI

A user interface designed to implement the **[Trojan-Go](https://github.com/p4gefau1t/trojan-go) API** to manage users or monitor the server.

![intro](https://user-images.githubusercontent.com/123581768/217651701-c6e8a15f-4aca-4350-8650-636f7d8eb948.png)


Written with C++ and compiles to webassembly which allows fast encryption/decryption of packets being 
sent/received from server &  uses a  modern bloat free ui-  library [Dear ImGui](https://github.com/ocornut/imgui)

# Install
## Linux
>**Tested on Ubuntu 20**


```sh
wget  "https://raw.githubusercontent.com/Leiren/Npanel/master/scripts/install.sh" -O install.sh && chmod +x install.sh && bash install.sh
```

>If you want to update the panel, you should backup first and then install new version (above script) then place users.db and panel.json to /opt/Npanel

## Windows

>**Tested on Windows 10**

>Download the latest release and run .exe , if you want to use it on your home Windows pc rather than a Windows server, you should configure your home router to forward ports 80,443 .

>**Important Notice on Windows:**
on first startup of the program (setup stage) you must allow ports 80,443,2060 in firewall settings by your self!
then open http://yourip:2060 on your browser and finish the setup stage.
after that, only ports 80,443 are required to be allowed in firewall settings.





#	Backup
 Npanel on Linux must be placed inside /opt folder so
 - In order to backup your users: /opt/Npanel/users.db
 - In order to backup your settings: /opt/Npanel/panel.json
 - But it is suggested to Backup the folder /opt/Npanel entirely.
 
 on Windows The Npanel folder is your backup indeed.
 # Transfer
on Linux you should backup /opt/Npanel Folder on old server then
- install npanel using install script on destination server.
- replace /opt/Npanel with your backup, then
- service npanel restart

on Windows you can just copy the Npanel folder and move it to destination server since it is portable.


# Uninstall
on Linux:
- service npanel stop
- rm -rf /opt/Npanel
- rm /etc/systemd/system/npanel.service
# Notes
 - This UI is only a front-end application and it is useless by it self, you must implement your server side functions by your favorite language like python/c/etc.. or use the provided server which has conditions.
 
 - current server support always disables ipv6 , enables bbr , disables ufw to avoid problems. (Linux only)
 
-  current server support  always kills ports 80,443 (for global serving) and ports 2060,2061 for local listening at startup. 
- during the setup wizard, you configure the server by connecting to port 2060; but after setup is finished only ports 80 , 443 are opened globaly and ports 2060,2061 are used locally.
 - This project is under active development. you are welcome to report bugs.
 
-  If you want to reduce the risk of your server getting blocked, tell your users to use clients that support uTls. (lastest version of most clients do it)
