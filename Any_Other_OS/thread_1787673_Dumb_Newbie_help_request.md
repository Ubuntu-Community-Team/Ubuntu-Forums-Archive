---
title: "Dumb Newbie help request"
date: 2011-06-21
forum: Any Other OS
---

### Post by Stewart54 on 2011-06-21
Not sure where to post this so I thought that I would start here.  New to Linux and enjoying the learning experience.  Have Ubuntu 11.4 plus Linux Mint loaded on my computer. At boot I just let it default to Ubunu and open.  Today I thought that I would try Mint, so I started up and at the screen that gives program options I highlight Linux Mint, which starts to load, and than goes to terminal.  Where do I go from there to complete Mint loading.

Can shut machine down and restart and it will load up Ubuntu no problems.

Would appreciate any help you can offer

Thanks

Stewart

---

### Post by Perfect Storm on 2011-06-21
Moved to Other OS/Distro Talk.

---

### Post by Rubi1200 on 2011-06-21
Hi and welcome to the forums Stewart54 :)

What version of Mint did you install and what graphics card do you have?

In my opinion, the best thing to do is post the results of the boot info script so we can see what is going on:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Stewart54 on 2011-06-21
Hey Rubi,

Hope this makes some sense.  tried to load and extract boot info script per link and get the following in terminal
stewart@stewart-MS-7599:~$ sudu bash ~/Downloads/boot_info_script.sh
No command 'sudu' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'tudu' from package 'tudu' (universe)
sudu: command not found
stewart@stewart-MS-7599:~$ bash ~/downloads/boot_info_script.sh
bash: /home/stewart/downloads/boot_info_script.sh: No such file or directory
stewart@stewart-MS-7599:~$ 

If this makes sense I am running mint 10 KDE and Ubuntu 11.04.  When setting up loaded Mint first, and let Ubuntu partition and load , basically 500 gb each.  Used mint for a week or 2 and than loaded Ubuntu from disc, and have never been able to figure out how to get back to Mint either at boot up, or switching " on the fly " if that can be accomplished.

Have a GeForce 210 Nvidia 270.41.06 video card installed, and have updated drivers but than get a message on the update screen that driver is installed but not currently in use.

Have been following posts on that, and to date have seen nothing that seems to be an easy or correct fix.

Hope this makes some kind of sense.

When Mint goues into terminal, I will log in and passward and it prints some funny lines ending with "i will live to be a grandparent"

Keyboard seems to be the only think working at that point as I move the mouse and it is not seen

Thanks

Stewart

---

### Post by Rubi1200 on 2011-06-21
Use this guide to set nomodeset as an option when booting:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

See the section on how to set options on an installed system. If it works, enable the drivers for your card.

---

