---
title: "Not a noob - sure feel like one; need help with runlevel"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Psquared on 2007-01-16
OK - here goes. My system is setup this way:

1 HDD with 4 partitions, and a swap file.

hda1 Zenwalk 4.2 Linux w/lilo
hda2 empty - future use
hda3 empty - future use
hda4 (Kubuntu - not working; I botched it)
hda5 (swap)

I tinkered too much with hda4 and finally borked it. :-k  I had some important data on it and I had a Zenwalk 4.2 (latest) iso, so I decided to install it on hda1. I did some prep work by using gparted rescue disk and formatted hda1, hda2, and hda3 with ext3.

Now, I got Zenwalk installed and mounted hda4 and got my data onto hda1. (Zenwalk) The last thing I was going to do was install the nVidia drivers. The instructions said I had to exit x using cntl-alt-f2 and/or telnit3 or init3. When I did that I kept getting the konsole login and when I would try to login it said my password had "expired" Please contact your administrator. Ha - call myself?? ](*,) ](*,) 

I had the bright idea to edit inittab to runlevel3 and reboot. I did that and guess what .... yep, couldn't login. Said my password had expired. So how am I going to get back into Zenwalk?? :-k 

OK - I had the Kubuntu Live CD so after trying the Rescue CD and finding it of no help, I booted the Kubuntu Live CD and mounted hda1. That worked and I could actually bring up the inittab file for Zenwalk. However, when I changed it back to runlevel 4 I couldn't save it. Said I didn't have permission. Another error had to do with kedit or kate or nano not being able to communicate with the Xserver. :confused: 

Now I thought with a live CD root access was easy and a file like inittab could be changed rather easily. Zenwalk makes you setup a user id and password and then the old su password. Maybe sudo from the Kubuntu Live CD isn't enough to change a Zenwalk conf file like inittab?? 

My solution is to reinstall Zenwalk or install Kubuntu on hda1 and then put Zenwalk and the other distros I want to try (Fluxbuntu and Vector Linux) on the other partitions. It's just such a pain to go through reinstalling just to change one number. Surely there has to be an easy way.

Anyone got any ideas? Thanks.

---

### Post by bodhi.zazen on 2007-01-16
> **Psquared said:**
> Anyone got any ideas? Thanks.

What a tangled web we weave :p

How do yo like Zenwalk? My wife uses it as her primary OS :p

Open kate (or vim or nano) with root power !

```
gksudo kate /file/to/edit

or 

sudo vim /file/to/edit

or 

sudo nano /file/to/edit
```

Also you can change run-levels with sudo init x where x = runlevel

Also you can change your PW with:

sudo passwd <user_name>

HTH 8)

---

### Post by Psquared on 2007-01-16
> **bodhi.zazen said:**
> What a tangled web we weave :p

How do yo like Zenwalk? My wife uses it as her primary OS :p

Open kate (or vim or nano) with root power !

```
gksudo kate /file/to/edit

or 

sudo vim /file/to/edit

or 

sudo nano /file/to/edit
```

Also you can change run-levels with sudo init x where x = runlevel

Also you can change your PW with:

sudo passwd <user_name>

HTH 8)

> 

ubuntu@ubuntu:~$ sudo nano /home/ubuntu/"mount point"/etc/inittab
ubuntu@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
ubuntu@ubuntu:~$ root
bash: root: command not found
ubuntu@ubuntu:~$ sudo root
sudo: root: command not found
ubuntu@ubuntu:~$ su root
Password:
su: Authentication failure
Sorry.
ubuntu@ubuntu:~$ sudo root
sudo: root: command not found
ubuntu@ubuntu:~$ su root
Password:
su: Authentication failure
Sorry.
ubuntu@ubuntu:~$ su root
Password:
su: Authentication failure
Sorry.
ubuntu@ubuntu:~$  

None of those combos work. Remember, I am running the Kubuntu Live CD. I gain access to hda1 by mounting. It shows up as /home/ubuntu/<mount point>.

From there i can open a file browser and navigate to the inittab file, but I cannot save any changes whether i used su, sudo, gksudo. I tried opening inittab with nano and kate by typing su, sudo, and gksudo /home/ubuntu/"mount point"/etc/inittab but came up empty. I tried navigating directly to the file and opening it with su, sudo, and gksudo with kate and nano, but to no avail.

I am going to try your trick with changing the password by rebooting to Zenwalk. (BTW, Zenwalk is a pretty good little distro, but getting nVidia driver installed looks like it will be a bear.

---

### Post by k1001001 on 2007-01-16
To log into root in Ubuntu, use the command:
```
sudo su
```
After you type your password, you should be logged into root. Here's how mine works:
```
keith@keith-laptop:~$ sudo su
Password:
root@keith-laptop:/home/keith#
```
And to exit root, just type "exit."

Also, Ubuntu terminal does not really support filenames with spaces. Therefore, the file /home/ubuntu/"mount point"/etc/inittab probably will not work because of the space in "mount point". I could be wrong though. I could also be misunderstanding what you mean there as well.

Another thing, gedit will probably be a better file viewer for you, instead of nano or kate. Gedit does the same thing, but with a nice looking GUI instead of command-line and keyboard  shortcut combos. Try it:
```
sudo gedit /file/to/view
```

---

### Post by bodhi.zazen on 2007-01-16
LOL :lol:

To become root on the live cd it should be:```
sudo su
```

I am not sure, but I do not think the kubuntu CD has gedit so I think Kate will be best.

You can use a space in file names as long as you use quotes or an excape:

mount\ point or "mount point"

Try this:```
sudo mkdir /media/zenwalk
sudo mount /dev/hda1 /media/zenwalk
gksudo kate /media/zenwalk/etc/inittab
```

If you are root you will not need sudo/gksudo

FYI:

sudo = not gui commands

gksudo = gui (for say kate, gedit, konqueror)

HTH :)

---

### Post by Psquared on 2007-01-17
Thanks guys. I fixed it.

I mounted hda1 in /media by going root and the command:

mount /dev/hda1 /media

I was able to invoke nano as root and get into the inittab file and make my change back to runlevel 4 and save it.

Then I was able to reboot Zenwalk and get into the gui.

The thing about the password expiring had me confused. What I found out is that in Zenwalk user passwords have expiration dates. By using the system configuration I was able to change the expiration from a specific date to "never."

Unusual arrangement, but good safety precaution. I've never really liked the way Ubuntu sets up root access with Sudo by default. Zenwalk is pretty neat. The best implementation of Xfce I've seen - better than Xubuntu in my opinion.

Getting ready to try Vector Linux, Elive and Fluxbuntu. 

Man this is fun.  :p

---

