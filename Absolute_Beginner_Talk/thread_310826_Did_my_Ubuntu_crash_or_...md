---
title: "Did my Ubuntu crash? or .."
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-01
Hello, I am running Ubuntu 6.10, granted I am a NooB, have been using Ubuntu without any significant problems.
Earlier today, I was connected to my Ubuntu machine from work (XP) through ssh, as well as a parallel connection through vnc (x11vnc), and listening to my songs stores on my computer through a browser, when all of a sudden, everything crashed. SSH connection lost, as well as Vnc, and no webserver. I had no idea what had happened and couldn't remotely access my machine for the entire day. 
Coming home, I found my computer with the display off  but the computer still on.  Moving the mouse, hitting keys, <ctrl alt del> nothing seemed to bring the machine back up. I had to manually reboot, and couldn't even reboot into Ubuntu, all I got was a bank screen that stayed there for minutes. I then rebooted to my XP partiotion and rebooted back to Ubuntu. Everything seemed to be working then. 

Having all these daemons running (sshd,apache,vncserver) had me paranoid as I had been getting the automaded ssh breakin attempts on a daily basis.  But I couldn't find anything out of the ordinary on the logs (auth.log, daemon.log, sys.log xorg.log)


1 .How can I figure out what had happened to make my Ubuntu machine unresponsive? (what log files do I need to look at?)

2. Does Ubuntu crash per se as a windows machine would?

3. Although I had disabled root logins on my sshd, I still can not figure out how to get my rsa public key on XP and have putty recognize it (tried copy the output in the rsa_pub and pasting on a notepad in windows and naming it as a .ppk file for putty to use to no avail) Is the answer using scp to copy the file from ubuntu to Xp and renaming it?

appreciate all your comments and suggestions in advance..

---

### Post by ewl1217 on 2006-12-01
I don't know what the crash was all about, but I can help with the ssh keys. You'll need to download puttygen.exe from the PuTTY site. Using that, Go to Conversions > Import (it goes something like that). Open your ssh private key from Ubuntu. It should prompt you for a passphrase. After that, click the button to save your private key. Now it should work with PuTTY.

---

### Post by habtish on 2006-12-04
> **ewl1217 said:**
> I don't know what the crash was all about, but I can help with the ssh keys. You'll need to download puttygen.exe from the PuTTY site. Using that, Go to Conversions > Import (it goes something like that). Open your ssh private key from Ubuntu. It should prompt you for a passphrase. After that, click the button to save your private key. Now it should work with PuTTY.

 I followed your instructions and downloaded the puttygen.exe clickinig on Conversions and import key opens up an explorer window which looks for the key file on the windows machine and doesn;t give the option to import it from a remote location. So I used scp to get my id_rsa.pub file on the windows machine, and pointing puttygen to that file wouldn't work.. changed the file extension to .ppk [a putty public key file format] and it was still telling me the format was invalid... Don't know what to do next...](*,)

---

### Post by BeachBum on 2007-01-29
> **habtish said:**
> 
1 .How can I figure out what had happened to make my Ubuntu machine unresponsive? (what log files do I need to look at?)

2. Does Ubuntu crash per se as a windows machine would?

3. Although I had disabled root logins on my sshd, I still can not figure out how to get my rsa public key on XP and have putty recognize it (tried copy the output in the rsa_pub and pasting on a notepad in windows and naming it as a .ppk file for putty to use to no avail) Is the answer using scp to copy the file from ubuntu to Xp and renaming it?



1. Check /var/log/syslog and /var/log/messages

2. Not sure about your question; my box has crashed occasionally, but only when provoked by me.

3. [http://www.unixwiz.net/techtips/putty-openssh.html](http://www.unixwiz.net/techtips/putty-openssh.html)

**To further secure sshd**
1. PermitRootLogin no
2. Run sshd on a different port, >10000 or something large (or, if you're behind a router, you can block port 22 and setup an uncommon public port to trigger port 22 privately)
3. Use the AllowUsers and DenyUsers lines in sshd_config; AllowUsers user1 user2 
4. StrictModes yes
5. PermitEmptyPasswords no
6. PasswordAuthentication no (this means you can ONLY login if you have the corresponding private key generated in the steps above)
7. [http://www.ubuntuforums.org/showthread.php?t=254149&highlight=denyhosts](http://www.ubuntuforums.org/showthread.php?t=254149&highlight=denyhosts)

Also, you were able to login to your Ubuntu machine from work without using keys for ssh, meaning you either had passwords or no passwords, which is fairly unsecure nowadays.  Just because the logs don't show anything doesn't mean someone could have messed with your machine.  To be safe, I would backup any critical media files or documents and reinstall the operating system; there is no telling where any malicious software was installed, if at all.  Once you get back up and running, make the changes to secure sshd as mentioned above before you start the daemon.  

Hope that helps.

---

