---
title: "Permissions problem - no audio, USB, unzipping"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Books on 2006-10-21
[SIZE="2"]I've had a massive permissions problem since upgrading to Dapper. At first I thought that it was a USB problem because I first noticed that I couldn't print to my printer. It would send the print job to the printer but nothing would happen. Back in July I posted this question -- [USB devices are missing after Dapper]("http://www.ubuntuforums.org/showthread.php?p=1310561") -- but we never could solve it.

Since then I've found out that the problem is MUCH more widespread.

- I have no audio but the media players all think they are playing. (Yes, I have the speakers on. ;) )

- I can't unzip any compressed files from any partition other than the Linux home partition. When I try it says I don't have permission.

- Very often I can't move/copy/delete files from one partition to another, and it puts up an error message saying I don't have permission.

- I can't print, but the KDE and Gnome printer utilities think they are printing.

- I can't use my external USB hard drive if it is on when I boot up, but I can use it if I turn it on after I've logged in.

Does anyone have any ideas what to try? This has plagued me since July and I have to log into Windows just to print anything.

*Thank you* for any help you can offer!!!

Books[/SIZE]

---

### Post by mark_g on 2006-10-21
I've had the same problem after adding a new user. The problem was that that user wasn't a member of the correct groups. 
Try adding the username to the correct groups in /etc/groups by appending them with ,username to udev and alike.

Let me know if it helps or you need a better explanation.

---

### Post by Books on 2006-10-21
[SIZE="2"]Thanks, mark_g

I don't have a file 'etc/group*s*' but there is an 'etc/group' and an 'etc/group-'. Is there supposed to be a etc/groups - plural "S"?

The 'etc/group' file reads:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:books
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:books,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:books,hal,haldaemon
floppy:x:25:books,hal,haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:books
dip:x:30:books
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:books
sasl:x:45:
plugdev:x:46:books,hal,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
books:x:1000:
lpadmin:x:104:books
scanner:x:105:books,cupsys
admin:x:106:books
crontab:x:107:
ssh:x:108:
slocate:x:109:
messagebus:x:110:
hal:x:111:
saned:x:112:
postfix:x:113:
postdrop:x:114:
clamav:x:115:
gdm:x:116:
haldaemon:x:117:
ssl-cert:x:118:
```

I tried to look at the 'etc/group-' but it says:
*You do not have enough permissions to read file:///etc/group-*

There isn't a 'udev' section like you mention in your post... is this the problem?

This may or may not be related, but there is an error message very quickly during bootup that says "udevd-event [3295]: wait_for_sysfs: waiting for 'sys/devices/platform/i82365.0/bus' failed". It also says something about 'pcmcia' start failed.

Books[/SIZE]

---

### Post by mark_g on 2006-10-22
It's the /etc/group file and the plugdev device instead of udev. I was on a Windows pc at the time of posting, so couldn't check it.

I can see in your group file that you have a user called 'books'. This user is a member of the audio group. Your soundcard is owned by the audio group, so if you're a member of the audio group, you have permission to use this device and play music.

audio:x:29:books

So if, for example, you add a new user and want to give it permission to play music, you can add this user by editing the file:

> sudo gedit /etc/group

audio:x:29:books,newusername

or you can use the command

> sudo adduser username groupname

This is how I solved my problem, don't know if your case is exactly the same.

---

### Post by Books on 2006-11-04
> **mark_g said:**
> I can see in your group file that you have a user called 'books'. This user is a member of the audio group. Your soundcard is owned by the audio group, so if you're a member of the audio group, you have permission to use this device and play music.

Thanks, mark_g

The strange thing is that I am the user "books" on my system and there aren't any other users. I'm listed as a user in the audio group, but still no audio.

Books

---

