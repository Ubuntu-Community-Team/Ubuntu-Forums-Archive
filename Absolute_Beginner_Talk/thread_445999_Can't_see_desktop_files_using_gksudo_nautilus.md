---
title: "Can't see desktop files using gksudo nautilus"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-05-16
I have downloaded Thunderbird 2.0 onto my desktop. I want to move the extracted file to a folder using gksudo Nautilus so I can use launcher to start Thunderbird. However, when I run gksudo Nautilus and double-click Desktop the two files (the tar,gz and the extracted file) do not appear. How do I get them to appear in Nautilus? I turned up nothing on a search to find help to resolve this.

BTW, I am using Feisty 7.04.

Thanks for your help.

---

### Post by taurus on 2007-05-16
When you run "gksudo nautilus", you are running it as root but I assume you saved your thunderbird as a user.  Therefore, you need to navigate to /home/**username**/Desktop.

You do know that you can create a short cut on the panel to start thunderbird if you want.  You don't have to move it anywhere else as root.

---

### Post by aysiu on 2007-05-16
Well, first of all, [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird) will install Thunderbird 2.0 for you.

Secondly, when you start *gksudo nautilus*, Nautilus defaults to viewing the /root folder, not the /home/username folder.

---

### Post by alienexplorers on 2007-05-16
You must navigate to [COLOR="Red"]/home/username/desktop[/COLOR] to view the desktop files.

---

### Post by kittyhawk63 on 2007-05-16
> **taurus said:**
> When you run "gksudo nautilus", you are running it as root but I assume you saved your thunderbird as a user.  Therefore, you need to navigate to /home/**username**/Desktop.

You do know that you can create a short cut on the panel to start thunderbird if you want.  You don't have to move it anywhere else as root.

Well, that is really what I am trying to do. Can you explain how you would do this. Thank you, Taurus.
kh

---

### Post by kittyhawk63 on 2007-05-16
> **aysiu said:**
> Well, first of all, [this script]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird") will install Thunderbird 2.0 for you.

Secondly, when you start *gksudo nautilus*, Nautilus defaults to viewing the /root folder, not the /home/username folder.

Thanks. I didn't know that.
kh

---

### Post by kittyhawk63 on 2007-05-16
> **alienexplorers said:**
> You must navigate to [COLOR=Red]/home/username/desktop[/COLOR] to view the desktop files.

Thanks. You and Taurus are on the same page.
kh
You confirmed what Taurus said. And, I trust Taurus.

---

### Post by aysiu on 2007-05-16
> **kittyhawk63 said:**
> Well, that is really what I am trying to do. Can you explain how you would do this. Thank you, Taurus.
kh
If, for example, you extracted the Thunderbird folder to /home/username/Desktop/thunderbird, you could right-click the applications menu, edit the menu, and create a new menu entry with the command ```
/home/username/Desktop/thunderbird/thunderbird
``` and the icon /home/username/Desktop/thunderbird/icons/mozicon48x48.xpm (or something like that--poke around to find the actual filename).

---

### Post by kittyhawk63 on 2007-05-16
> **aysiu said:**
> Well, first of all, [this script]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird") will install Thunderbird 2.0 for you.

Secondly, when you start *gksudo nautilus*, Nautilus defaults to viewing the /root folder, not the /home/username folder.

I couldn't get the script to work. Do I copy the script line for Terminal starting with the word "**bash**" or start after the tilda "**~**" ?

kh

---

### Post by aysiu on 2007-05-16
It should look like this, with the bold type being what you type: ```
username@ubuntu:~$ **cd ~/Desktop**
username@ubuntu:~$ **chmod +x installnewthunderbird.sh**
username@ubuntu:~$ **./installnewthunderbird -install**
```

---

### Post by dannyboy79 on 2007-05-16
well if you downloaded the script to your usernames Desktop directory you want to run the command just how the guide stated:

bash ~/Desktop/installnewthunderbird.sh -install

but you do need to make ist executable first bu issuing this

sudo chmod +x ~/Desktop/installnewthunderbird.sh

if you can't get that to work an easier way to get this to run is to just navigate to whereever you downloaded the script to and simply run it using this command

./installnewthunderbird.sh -install

you don't need to specifiy bash because the shell is suppose to use is defined within the script but not all scripts will have this defined so some scripts you need to run and dfefine which shell you want it to use.

---

### Post by kittyhawk63 on 2007-05-16
Thanks guys. I should get this to work with your fine instructions. I will mark this "resolved."
kh

Thanks gain.

---

