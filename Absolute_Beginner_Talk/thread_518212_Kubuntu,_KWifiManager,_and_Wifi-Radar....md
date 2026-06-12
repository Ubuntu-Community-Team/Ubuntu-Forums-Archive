---
title: "Kubuntu, KWifiManager, and Wifi-Radar..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by stego_s_aurus on 2007-08-05
Hello all!
  I've come to find out that the best Wifi management combination for Kubuntu seems to be using both the default **Kwifimanager** And **wifi-radar**: **Kwifimanager** for the strength bar and general monitor, and **Wifi-Radar** to configure and automagically switch between multiple wifi networks and to connect to them, ala Windows. (Stir in some wifi-supplicant into the mix and you've got a great setup).

Anyway, One of the annoying bits I was encountering was the fact that kwifimanager uses the ugly and hard to use **kcmshell 'kcmwifi'** by default to configure the wifi networks that its connecting to, and Many people have complained how difficult it seems to be to just get the network to "load on startup" like it should, whereas Wifi-Radar seems to do the trick, but needs to be launched seperately. Now wouldn't it be wonderful if one could, from within KwifiManager, just click the Settings > Configuration Editor menu option and have it automatically open up wifi-manager??

Welp, using some old-skool file editing, I got it to do just that, Without having to recompile the kwifimanager program from source or do anything "super advanced" which means that newbies can do this, provided they follow instructions.

Follow these instructions, and you should be able to do the same (By the by, I did this in Ubuntu Feisty. Other versions of ubuntu will vary):

1) Make sure to have Midnight Commander installed (sudo apt-get install mc) and that you are Out of kwifimanager (It should not be in the system tray. If it is, right click it and click QUIT)

2) Launch Midnight Commander as Root (sudo mc)

3) type in "cd /usr/bin" and press ENTER

4) press the PAGE DOWN key on your keyboard until you get to the files that start with the letter k , and then use your arrow keys to highlight **kwifimanager**

5) We will first back this file up: press **F5** on your keyboard, and type in ***.bak** (Asterisk Period b a k) on the to: line, and press ENTER. You should now see the backup copy of the kwifimanager file in the list.

Take Note of the File Size. When you are Done editing this file, it MUST BE THE SAME SIZE!!!

6) with kwifimanager still highlighted, Press F4 to start editing. You will be taken into Midnight Commanders Editor.

7) We will now search for the string **kcmshell**: press **F7**, type in **kcmshell**, press ENTER. The editor will take you to the first occurance of the kcmshell command and highlight it in yellow.

NOTE that the command is prefixed by and followed by a period. If you move the cursor to the right, you'll see that the command used by kwifimanager is all here: **.kdesu.kcmshell.kcmwifi.** 

What we need to do is to replace the .kcmshell.kcmwifi. with .wifi-radar      .  (where there are 6 spaces after the wifi-radar command. DO NOT ERASE THE DOTS BEFORE OR AFTER THIS COMMAND!!! THESE ARE -NOT- PERIODS!!!

8) Tap the INSERT key once: up in the upper left, to the right of the filename, you should now see [---O], indicating that you are in OVERWRITE mode.

9) Move the square cursor until the letter k in kcmshell is highlighted.

10) start typing: wifi-radar       and six spaces. STOP after the kcmwifi command is erased.

11) press F2 to Save the file. press F10 to exit the editor.

12) LOOK at the file sizes of the two files, kwifimanager and kwifimanager.bak. they should be IDENTICAL. if not, something was missed: copy the original kwifimanager.bak file to kwifimanager and start again.

13) Now, via its icon, run the kwifimanager. You should see it launch and show the icon in the system tray. Then, click on Settings > Configuration Editor, type in your password, and wifi-manager should now launch.



It worked for me, I sure hope it can help others with this little annoyance!!

---

### Post by milosz.galazka on 2007-08-06
Thanks for info,
Did you tried knetworkmanager? I am using it and works good for me.

---

### Post by antilog on 2008-07-20
Running:
Dell Inspiron e1405
Kubuntu 8.0.4.1 KDE4
wifi-radar

When disable WPA on my AP, I can connect and get a DHCP IP.  When using WPA (wext), I cannot get an IP.  I'm guessing the WPA is failing.  Also, I can't get WEP to work either.

I don't want to hard code SSID connections, as it is a laptop and I am often on different networks.

Any ideas?

---

