---
title: "White screen display on monitor"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by saege on 2006-11-01
Hi  Guys,

I am new to ubuntu and linux . Probably mine is a simple proble. I went throught the forum and dint find any solution regarding my problem

My problem is that after installation of xubuntu 6.10 and subsequent booting of pc and logging into the OS all i see is a white display on the screen.
Prior to installation i had this problem when i was checking the LIVECD of this Distro.
Inorder to get the desktop back i had to press F3 in the LIve CD mode and change the disply settings from VGA to my standard 800 x 640. 
Since after installation i dont get the option of chnaging the display I cannot see the desktop but instead a white screen?

Could any one tell me how to go about on this situation.

---

### Post by Kateikyoushi on 2006-11-01
Try to reconfigure xorg.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by saege on 2006-11-02
> **Kateikyoushi said:**
> Try to reconfigure xorg.

```
sudo dpkg-reconfigure xserver-xorg
```

I am a new bei
Do mind me for asking where can i type this code? coz i cant see the desktop . could you tell me where i can type this command

---

### Post by NeoLithium on 2006-11-02
Just open yourself up a terminal window, and type that string in; and you'll be on your way :)

---

### Post by Kateikyoushi on 2006-11-02
Press CTRL+ALT+F2 after the screen turns white, then login and type in the following command and configure X.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by saege on 2006-11-02
> **Kateikyoushi said:**
> Press CTRL+ALT+F2 after the screen turns white, then login and type in the following command and configure X.

```
sudo dpkg-reconfigure xserver-xorg
```

when i press CNTRL+ALT+F2 the monitor goes blank even though there is power on the monitor now there is no display? ANy hints on these?

---

### Post by saege on 2006-11-03
Guys dont desert me just help me out???

---

### Post by Kateikyoushi on 2006-11-03
Then at the logon select from graphical environments the terminal.

---

### Post by saege on 2006-11-03
I have this white screen display problem appearing at the logon page. I tried with Mandriva also and still have the same problem. BUt i have no problems with windows xp as i have dual boot on my PC . Should it be a graphics card problem which gets affected with linux. 
But then why does that happen coz with Xubuntu 6.10 Live CD option i have perfect display. And only when i install it on the HDD i have this white display interlaced by lines.

Any options to get this error corrected?

Thanks

---

### Post by Kateikyoushi on 2006-11-03
You can boot to terminal by selecting the single user mode line in the grub menu, then you won't boot to graphical mode and can run the command.

---

### Post by saege on 2006-11-03
when i get in to the single user mode I get the following prompt.

sh-3.00#  when i tried to put the above code there it showed some error message.

Are there any commands to start the terminal window from the single  user mode?

---

### Post by blendmaster on 2006-11-03
This may be a dumb suggestion, but have you tried rebooting in safe mode?

It gives you the terminal automatically there.

---

### Post by saege on 2006-11-04
is there any other safe mode in linux other than failsafe in the case of Mandriva?

---

### Post by BungaMan on 2006-11-09
use the following commands to fix the white screen problem (it worked for me).  

first, in a console cd to the home dir of the user which has this problem.

$ cd /home/<username>

Next remove all files with a lock related to gconf (this can be one of the causes)

$ rm -rf .gconf*/*lock*

and then cd into .gconfd

$ cd .gconfd

and remove any saved states.

$ rm saved_state*

and that's it.

---

