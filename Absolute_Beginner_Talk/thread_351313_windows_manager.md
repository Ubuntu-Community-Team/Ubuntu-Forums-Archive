---
title: "windows manager"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by terb on 2007-02-01
using edgy eft-- i have tried to bringup x windows but can not. none of the ctrl-alt f--7 have any results except f3 which tells me that i am using ac power. i have done a search of the forums here and found an article on windows managers and now know a whole lot of thigs i did not but not what i really want to know. How do i access x windows?? i know i have a Gnome desktop and i know my windows manager is Metacity. i can not "dial out" yet but have  tried to install what i think is important with cds burned in xp. sure would appreciate anyone heading me in the right direction.
                                         thank you

---

### Post by aktiwers on 2007-02-01
Sorry.. but I really dont understand what you are asking?
Do you want to install a new Window Manager?
Or what is your problem exactly ?

---

### Post by shareMenaPeace on 2007-02-01
To get a quick start you can use an automatic installer which comes with the most needed things, like codecs and player etc.

You can get it here
getautomatix.com just download the installer and run it after download.

After this you can find it under applications.

Not sure what type of internet connection you have?

For cable you can use sudo pppoeconf from a terminal.

---

### Post by terb on 2007-02-02
thank you aktiwers-- sorry i guess i was wandering as i seem to have quite a few problems. my basic problem, for now, is i want to get out of CLI and into GUi. i have no success with ctrl-alt-f-- numbers except f3 which tells me i am using ac power. i know i am not doing something right  and would appreciate someone going through the steps necessary to work in x windows.
thank you shareMenaPeace for th information on the auto installer i shall certainly get it. as for my internet problem i will work around it for now.

---

### Post by steve.horsley on 2007-02-02
Do you get a prompt asking you to log in? (You may need to press Enter)
If so, have you succeeded in logging in?
If so, what happens if you type **startx** and press Enter?

We really need to know what you're seeing in front of you.

---

### Post by terb on 2007-02-02
well--- i could not get any action with ctrl-alt-f6 and enter. but with startx igot the following
host name: host name look up failure
xauth.        createing new authority file /home/bert/serverauth. 4802


x user not authorized to run xserver  aborting
could not get a file description refering to the console

on another try i got-- if server is no longer running. remove /tmp/ .XO -lock
 i really appreciate your time and effort on this

---

### Post by steve.horsley on 2007-02-03
That host name lookup failure looks suspicious to me. Can you post the output from theses commands:
[B]cat /etc/hosts
cat /etc/hostname[/B]

hosts should have a line starting 127.0.0.1 and listing both localhost and your hostname.
hostname should containn just your hostname. Both files must have exactly the same hostname. This is mine:

> steve@StevesPC:~$ cat /etc/hosts
127.0.0.1       localhost StevesPC

<other boring stuff cut out for brevity>
steve@StevesPC:~$ cat /etc/hostname
StevesPC
steve@StevesPC:~$ 


If they don't agree, or if the host name is missing, edit them to correct them with this command:
[B]sudo nano /etc/hosts
sudo nano /etc/hostname[/B]

But sudo may not allow you in, in which case you need to boot into recovery mode (which gives you a root login, and then do it.

---

### Post by terb on 2007-02-03
oh boy-- the cat/etc/hosts-- brought up "there is no file or directory" and the cat/etc/hostname did the same.
 i went to the network window and changed the hosts names and when i tried the --sudo nano /etchosts this came up "127.0.0.1 berts desk top" and " 127.0.1.1 berts desk top" the sudo nano /etc/hostname was "berts desk top". i tried the startx and it again said the"host lname look up failed. 
Steve i sure appreciate your help but until i can get online in ubuntu i think i will stop trying to configure this program. there is one more thing i would like to ask and that is how do i uninstall ubuntu. i reinstalled edgy eft to see if new entries would make any difference-- they didnt--- and i now have a whole bunch of ubuntu in the grub

---

