---
title: "Really new in Ubuntu... plz help."
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by AlexAv on 2007-02-09
Hi Im new on this OS then Im lost, very lost... the resolution its in 800x600 and doesnt apears the 1200 x 768 where can i change this ??? I ve messaged to malathia hoping her to help me but found this forum and think why not post here too ... the video card appears to be fine but the monitor itstaken for a generic one heres a list of hardware
monitor acerview 54e
vcard integrated in MS-6368 motherboardand apears to ba a trident 
pentium3
512 ram

hope someone could help me and if its not to much step by step in the how to do it cause as I said its all new for me but its a challenge that worth... Im trowingh my XP pc hehehe... thanx
ALEXAV:confused:

---

### Post by dahlbeck on 2007-02-09
Just search the forum here....it should work if you  edit your xorg.conf file
like this..
[http://ubuntuforums.org/showthread.php?p=2116036](http://ubuntuforums.org/showthread.php?p=2116036)

---

### Post by AlexAv on 2007-02-09
Thanx man Iwill check on it....

---

### Post by ESPOiG on 2007-02-09
what size is the screen 15" 17" 19" etc

then just try this

1. open the terminal
2. type "sudo passwd root"
and type your user password into the first choice then a password of your choice for the user root, unless you have allready done this
3. then type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak"
4. now type this "sudo gedit /etc/X11/xorg.conf"
4. once it is open go down the page until you see a section like this

Section "Screen"
            Identifier "Default Screen"
            Device "ATI Technolgies, Inc. Rage Mobility"
            Monitor "Generic Monitor"
            DefaultDepth 24
            SubSection "Display"
                         Depth 1
                         Modes "800x600 640x480"

5. now edit all the lines that have the resolution choices with the resolution that you want eg, 1024x768 1280x1024 are pretty standard, include them in the line like so

Modes "1280x1024 1024x768 800x600 640x480"

6. save the file and exit
7. press these buttons together "Ctrt Alt Backspace" and login again
8. now goto System>Preferences>Screen Resolution and there should be a better list of screen resolutions

---

### Post by ESPOiG on 2007-02-09
damn beaten to it :D, oh well i was just trying to make it easier, also if you do my way and it fails

1. press Ctrl Alt F1
2. login
3. and type "sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf"
4. then "sudo /etc/init.d/gdm stop
5. then sudo gdm start

or miss 4 and 5 and reboot

---

### Post by nalioth on 2007-02-09
> **ESPOiG said:**
> what size is the screen 15" 17" 19" etc

then just try this

1. open the terminal
2. type "sudo passwd root"
and type your user password into the first choice then a password of your choice for the user root, unless you have allready done this
3. then type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak"
4. now type this "sudo gedit /etc/X11/xorg.conf"
4. once it is open go down the page until you see a section like this

  I really must protest this.  Ubuntu was made without an active root password for a reason.  If you enable a root account,
1: you open yourself up to an increased chance of being exploited (root is a common user name in most *nix distros), which leaves only the password to be found out.
2: Ubuntu has certain services fixed so they respond to the use of "sudo" and when you use them from a root account they don't work so well.

If you need a superuser (root) terminal, use ```
 sudo -i
``` or ```
sudo -s
```

I've been using a sudo-only superuser model for 6 years and have never needed to enable the root account.

---

### Post by ESPOiG on 2007-02-09
ok i dont like user superuse but whatever everyone has there own opinion

---

### Post by AlexAv on 2007-02-09
hehehe im lost before the first sudo appears command not found 
???

---

### Post by uncreative on 2007-02-09
Why not just "Ssytem" "Preferences" Resolution?

---

### Post by jvc26 on 2007-02-09
> **ESPOiG said:**
> ok i dont like user superuse but whatever everyone has there own opinion
Opening up the root user does decrease the security of the system quite considerably. The sudo command has been included to keep the root inactivated. Instructions should I think give the sudo command in preference to any other. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Il

---

### Post by AlexAv on 2007-02-09
trying it gives this...

alexav@alexav-desktop:~$ "sudo gedit/etc/x11/xorg.conf"
bash: sudo gedit/etc/x11/xorg.conf: No such file or directory...

---

### Post by ESPOiG on 2007-02-09
> **Illuvator said:**
> Opening up the root user does decrease the security of the system quite considerably. The sudo command has been included to keep the root inactivated. Instructions should I think give the sudo command in preference to any other. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Il

thats all great but i dont want to get into a fight over something a petty as this like i said my opinion is my own and your is yours i dont care what other think your should be telling this guy we are trying to help and not diverting this post from what it should be a question on this guys screen reolution

---

### Post by ESPOiG on 2007-02-09
> **AlexAv said:**
> trying it gives this...

alexav@alexav-desktop:~$ "sudo gedit/etc/x11/xorg.conf"
bash: sudo gedit/etc/x11/xorg.conf: No such file or directory...

dont add the quotes "" they are there to specify what command i am giving

---

### Post by AlexAv on 2007-02-09
Or at least how to modify the preferences in the xorg.conf... its protected for readonly and cant change it ... like in here...

[http://ubuntuforums.org/showthread.php?p=2116036](http://ubuntuforums.org/showthread.php?p=2116036)

---

### Post by ESPOiG on 2007-02-09
> **AlexAv said:**
> Or at least how to modify the preferences in the xorg.conf... its protected for readonly and cant change it ... like in here...

[http://ubuntuforums.org/showthread.php?p=2116036](http://ubuntuforums.org/showthread.php?p=2116036)

it is read only for your user so when you edit it as root it is writeable

---

### Post by AlexAv on 2007-02-09
Ok ive done it but its still the same just 800 and 640 mmhhhh let me check for a little and reboot to see what happens ... thanx to all for help will be over her for a while 

Greets Alex

---

### Post by slimdog360 on 2007-02-09
write this one down peoples
```
sudo dpkg-reconfigure xserver-xorg
```

open a terminal and copy that into it. Follow the prompts, if you are unsure about something just keep pressing enter. Finally you will get to a bit about your monitor, there should be three options, simple, medium and advanced. Go simple first and if that doesnt sort it out go medium. 
It will ask you if you want to write the changes to you xorg.conf file, thats a big yes-a-roony right there.

After thats done and finished press ctrl+alt+backspace together.

Before that though here is how to make a backup just incase (so do this first). Again copy this command into a terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
that makes a backup

write this one down for later
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
you may need this incase you get some big black screen after you press ctrl+alt+backspace. All you will need to do is enter you name and password then type in the above code (the third one) and press ctrl+alt+backspace once again.

---

### Post by ndefontenay on 2007-02-09
If you want to edit as root, simply type in the command 

```
gksudo kate filetoedit
```

Avoid using root user. You can do virtually anything without root just using sudo and gksudo.

If you want to edit something that requires root privilege. Use sudo or gksudo.

---

### Post by AlexAv on 2007-02-09
Ok I drop it for now but tomorrow continues with it... thanx again to you all and sorry for the time you give to this moron hehehe greets to all... Alex

---

### Post by pay on 2007-02-09
> **AlexAv said:**
> trying it gives this...

alexav@alexav-desktop:~$ "sudo gedit/etc/x11/xorg.conf"
bash: sudo gedit/etc/x11/xorg.conf: No such file or directory...There should be a space between gedit and /etc and the x should be uppercase, ie```
sudo nano "/etc/X11/xorg.conf"
gksudo gedit /etc/X11/xorg.conf
```just copy and past them (either one they both do the same thing, just with a different text editor. Also, you can leave comments around the file that you want to open, but not the entire command.

---

### Post by nalioth on 2007-02-09
> **ndefontenay said:**
> If you want to edit as root, simply type in the command 

```
gksudo kate filetoedit
```

Avoid using root user. You can do virtually anything without root just using sudo and gksudo.

If you want to edit something that requires root privilege. Use sudo or gksudo.

 'kdesu' is for starting kde apps as superuser.

 'gksudo' is for starting gtk/gnome apps as superuser.

One should use 'sudo' in the console for superuser tasks.

Opening gui apps with "sudo" sometimes allows your user space permissions to be reassigned to "superuser", which leads to them not running when you call them.  gksudo and kdesu start these with the proper permissions.

---

### Post by ESPOiG on 2007-02-09
yeh what he said ^ but for a basic program like gedit or kate it is fine, sudo that is

---

