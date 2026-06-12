---
title: "How to start my script at startup(ONLY)  of the PC ?"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-05
How to start my script at startup(ONLY)  of the PC ? 
  
     
I know the stuff:
chmod +x /etc/init.d/name_of_script.sh
update-rc.d /etc/init.d/name_of_script.sh defaults
BBBUUUUTTT this is both STARTUP of PC and HALT/shutdown
    
   
Thank you very much !!!!
  
Patrick

---

### Post by spizkapa on 2005-11-05
[QUOTE=patrick295767]How to start my script at startup(ONLY)  of the PC ? 
  
     
I know the stuff:
chmod +x /etc/init.d/name_of_script.sh
update-rc.d /etc/init.d/name_of_script.sh defaults
BBBUUUUTTT this is both STARTUP of PC and HALT/shutdown
[/QUOTE]

Well, you know "some" stuff. First thing you need to do is "man update-rc.d". You will then find that the defaults can be overridden manually. You will need something like:

update-rc.d /etc/init.d/name_of_script.sh start number runlevel1 runlevel2

where number is the priority of when you want the script to be run during boot (consult the same man page for this) and runlevelX is the runlevel that you want the script to be started in.

As you will have read the man page by now, you will also find out that scripts of this form must accept a start, restart and stop parameters though you can just live with start, if you want. Just copy one of the standard ones and edit to your heart's content.

I don't blame you for being confused, the init scripts always baffle me too.

HTH.

---

### Post by patrick295767 on 2005-11-05
[QUOTE=spizkapa]Well, you know "some" stuff. First thing you need to do is "man update-rc.d". You will then find that the defaults can be overridden manually. You will need something like:

update-rc.d /etc/init.d/name_of_script.sh start number runlevel1 runlevel2

where number is the priority of when you want the script to be run during boot (consult the same man page for this) and runlevelX is the runlevel that you want the script to be started in.

As you will have read the man page by now, you will also find out that scripts of this form must accept a start, restart and stop parameters though you can just live with start, if you want. Just copy one of the standard ones and edit to your heart's content.

I don't blame you for being confused, the init scripts always baffle me too.

HTH.[/QUOTE]
  

Thx for ur reply...
I read the man of the update-rc.d...
I was very confused with the runlevels and not sure really after it. It's maybe my poor english, the reason I guess.
I found a webpage about it but It's still not so easy for me.
I thought that it would be easy.
    
I'll look in more details then later in man page & google...
  
Linux is not soo easy for newbies, but  we like it !!
   
Greetz'
  
Patrick

---

### Post by ubuntu_demon on 2005-11-05
here's an example with iptables-restore :

create a script in /etc/init.d 

sudo pico /etc/init.d/iprestore

```

#!/bin/sh
sudo iptables-restore < file

```

sudo chmod +x /etc/init.d/iprestore

sudo ln -s /etc/init.d/test  /etc/rc2.d/S15test
(this only creates the start in runlevel 2 with priority 15)

---

