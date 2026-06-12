---
title: "Unity on Mint"
date: 2012-12-14
forum: Any Other OS
---

### Post by Zane Pepper on 2012-12-14
I installed Unity on my Mint install, but when I log out and go to change the desktop environment, it is not on the list. Any ideas on whats up?  Also, I a not sure if this is the right section for this, sorry if it is wrong.

---

### Post by mansonfan78 on 2012-12-14
Unity isn't listed as "unity" even in Ubuntu - it's just listed as "Ubuntu" and "Ubuntu 2d".  What is on your list?  It could be under a different name.

---

### Post by lisati on 2012-12-14
*Thread moved to **Other OS/Distro Talk**.*

Although based on Ubuntu, Mint is a distro in its own right.

---

### Post by Zane Pepper on 2012-12-14
> **mansonfan78 said:**
> Unity isn't listed as "unity" even in Ubuntu  - it's just listed as "Ubuntu" and "Ubuntu 2d".  What is on your list?   It could be under a different name.

All I have is Cinnamon regular and 2D and 2 versions of Gnome classic.

> **lisati said:**
> *Thread moved to **Other OS/Distro Talk**.*

Although based on Ubuntu, Mint is a distro in its own right.

Whoops, sorry, I should have looked around better.

---

### Post by Frogs Hair on 2012-12-14
Unity 4.xx worked on Mint 12 but you would have see if it is still compatible. 12.10 no longer includes 2D by default and the unity version is 6.12.

---

### Post by Zane Pepper on 2012-12-14
> **Frogs Hair said:**
> Unity 4.xx worked on Mint 12 but you would have see if it is still compatible. 12.10 no longer includes 2D by default and the unity version is 6.12.

Forgot to specify, I am on Mint 14. Unity works because I can launch it from the terminal, but it is extremely inconvenient to do it that way.

---

### Post by Chdslv on 2012-12-15
> **Zane Pepper said:**
> Forgot to specify, I am on Mint 14. Unity works because I can launch it from the terminal, but it is extremely inconvenient to do it that way.

Install lightdm and your problem would go away. While installing, it'd ask, and you choose lighdm. :D

If you want Mint stuffm but with Unity, then install Precise, Quantal or Raring, add the Nadia repos--you can copy them from your Mint 14--add to the sources.list and update. Then, install anything you want from Mint.

When you look at the Precise, Quantal or Raring sources.list and the sources.list of Mint, you'd notice that you are silently disallowed openings to many Ubuntu repos, which is the mainstay of Mint though.  

Have a look here too. [http://ubuntuforums.org/showthread.php?t=2093725](http://ubuntuforums.org/showthread.php?t=2093725)

---

### Post by Zane Pepper on 2012-12-15
> **Chdslv said:**
> Install lightdm and your problem would go away. While installing, it'd ask, and you choose lighdm. :D

If you want Mint stuffm but with Unity, then install Precise, Quantal or Raring, add the Nadia repos--you can copy them from your Mint 14--add to the sources.list and update. Then, install anything you want from Mint.

When you look at the Precise, Quantal or Raring sources.list and the sources.list of Mint, you'd notice that you are silently disallowed openings to many Ubuntu repos, which is the mainstay of Mint though.  

Have a look here too. [http://ubuntuforums.org/showthread.php?t=2093725](http://ubuntuforums.org/showthread.php?t=2093725)

I have lightdm installed, but the problem is still there.

---

### Post by deadflowr on 2012-12-15
Your best bet is to install ubuntu-desktop.

---

### Post by Zane Pepper on 2012-12-15
I just gave up. I kinda like Cinnamon and I can always just switch back to Ubuntu 12.04 if I really miss Unity.

---

### Post by jshawver on 2013-04-28
Managed to get the option for unity to show up and work under sessions at the boot menu for Mint. A new file is needed under /usr/share/xsessions . I in particular called mine unity.desktop. Thus making the path /usr/share/xsessions/unity.desktop. To get it working simply type:
sudo vim /usr/share/xsessions/unity.desktop

and then enter:

[Desktop Entry]
Name=Unity
Comment=This session logs you into Unity
Exec=unity
TryExec=/usr/bin/unity
Icon=
Type=Application

finally. Save and close the file. Just as a heads up. I am using mints mdm, and the boot is rather slow. For this reason, I would recommend using lightdm as your default and then add this file. After this file is added, you will be able to see a new option called "Unity" in the session menu before you login. If you desire a different name to display in the session menu, simply change the value of Name=SomeNewNameYouWant. Hope this helps!

---

### Post by jshawver on 2013-04-28
[COLOR=#000000]Managed to get the option for unity to show up and work under sessions at the boot menu for Mint. A new file is needed under /usr/share/xsessions . I in particular called mine unity.desktop. Thus making the path /usr/share/xsessions/unity.desktop. To get it working simply type:[/COLOR]
[COLOR=#000000]sudo vim /usr/share/xsessions/unity.desktop[/COLOR]

[COLOR=#000000]and then enter:[/COLOR]

[COLOR=#000000][Desktop Entry][/COLOR]
[COLOR=#000000]Name=Unity[/COLOR]
[COLOR=#000000]Comment=This session logs you into Unity[/COLOR]
[COLOR=#000000]Exec=unity[/COLOR]
[COLOR=#000000]TryExec=/usr/bin/unity[/COLOR]
[COLOR=#000000]Icon=[/COLOR]
[COLOR=#000000]Type=Application[/COLOR]

[COLOR=#000000]finally. Save and close the file. Just as a heads up. I am using mints mdm, and the boot is rather slow. For this reason, I would recommend using lightdm as your default and then add this file. After this file is added, you will be able to see a new option called "Unity" in the session menu before you login. If you desire a different name to display in the session menu, simply change the value of Name=SomeNewNameYouWant. Hope this helps![/COLOR]

---

### Post by speartip on 2013-04-29
Can I just ask, purely out of curiosity, why would you want to install Unity on Mint.
Isn't the main reason for using Mint to get away from Unity.
I know Linux is all about choices, but if you want to use Unity, surely you install Ubuntu, & spend 10 minutes installing the restricted-extras, then tweaking the theme to look like Mint, or am I missing something???

---

### Post by CaptainMark on 2013-05-01
I think you need to install the indicator-session package, I had the same problem before and its just one single package your missing, I'm hoping my memory serves me okay because if not I don't remember what package you need

---

### Post by Rebelli0us on 2013-05-01
Check the menu in your login screen, it's there.

---

