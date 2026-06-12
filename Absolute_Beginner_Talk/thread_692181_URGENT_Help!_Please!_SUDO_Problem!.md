---
title: "URGENT Help! Please! SUDO Problem!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-09
I am very happy with Ubuntu so I can't post more often here, well only now.

I added the following lines to sources.list

```
deb http://download.tuxfamily.org/syzygy42 gutsy exaile
```

and

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
sudo apt-get update
sudo apt-get install exaile-bzr
```

while saving it it says I am not an administrator or a root, but I am so I went to this website and followed [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I think my mistake, I added my self over and over like sudo adduser karlo admin and sudo adduser karlo root

something like that, and then I figured out when reading the documentation carefully, I can use the GUI interface or sudo gedit sources.list

it did work, 
then I ran Updates thing of Ubuntu and it told me I have an invalid sources.list..

then received an error. then..

I restarted my PC because I can't access the Users and Groups,

Now look at my desktop.

And the menu here... very alarming.

Also, accessing the Edit Users and Groups from my username on the top right of the screen,  it must enter a password for group named "users-admin" ... I think it should be "karlo-laptop" ... guys help!!! Please I beg you, I don't want to reformat again.:confused:

---

### Post by taurus on 2008-02-09
Post the output of this command from a terminal.

```
id
```
And please do not add yourself to group root!  If you want to use sudo, then you should belong to group admin, NOT root.

Boot into recovery mode from GRUB menu and run

```
useradd admin karlo
shutdown -r now
```

---

### Post by karlo on 2008-02-09
> **taurus said:**
> Post the output of this command from a terminal.

```
id
```
And please do not add yourself to group root!  If you want to use sudo, then you should belong to group admin, NOT root.

Boot into recovery mode from GRUB menu and run

```
useradd admin karlo
shutdown -r now
```

upon entering what you've said the **id** thing, here's the result:

---

### Post by karlo on 2008-02-09
I've also tried what's suggested here [http://ubuntuforums.org/showpost.php?p=4300239&postcount=2](http://ubuntuforums.org/showpost.php?p=4300239&postcount=2)

Boot up recovery mode enter useradd admin karlo and still it does not work!

Although my desktop is restored.

I still can't see Users and Groups.

On the second pic, I can see it but when I click it, the following dialog box appeared, tried entering my password even a blank one, nothing happened. Please help help help!:(:confused:

---

### Post by jvc26 on 2008-02-09
Please don't double post about this issue, you already have one thread about this problem.

What is the output of:

```
cat /etc/group
```

Il

---

### Post by p_quarles on 2008-02-09
Duplicate threads merged. Please don't double-post.

---

### Post by karlo on 2008-02-09
> **Illuvator said:**
> Please don't double post about this issue, you already have one thread about this problem.

What is the output of:

```
cat /etc/group
```

Il

```
karlo@karlo-laptop:/etc/apt$ cat /etc/group
root:x:0:karlo
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:karlo
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:karlo
fax:x:21:karlo
voice:x:22:
cdrom:x:24:haldaemon,karlo
floppy:x:25:haldaemon,karlo
tape:x:26:
sudo:x:27:
audio:x:29:karlo
dip:x:30:karlo
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:karlo
sasl:x:45:
plugdev:x:46:haldaemon,karlo
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,karlo
nvram:x:105:
fuse:x:106:karlo
ssl-cert:x:107:
lpadmin:x:108:karlo
messagebus:x:109:
admin:x:110:karlo
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:karlo
haldaemon:x:116:
powerdev:x:117:haldaemon,karlo
gdm:x:118:
slocate:x:119:
karlo:x:1000:
ntp:x:120:
ntfs:x:1001:karlo
```

While waiting for someone to reply to my post, I googled everything.

In this Thread, someone replied me to use **adduser admin karlo**, but it should be **adduser karlo admin**.

based from *[http://ubuntuforums.org/showpost.php?p=3264403&postcount=5](http://ubuntuforums.org/showpost.php?p=3264403&postcount=5)*

Now, I think it is fixed, also I've fixed the **sources.list** from **/etc/apt**.

Also, I like what's happening right now, I think I'm becoming a little familiar and possibly a little expert with this command thingy(s).

Now, I still need some help, ah, the above CODE, is it messed up? How can I fix it?

Also I learned that If I can't run or the program can't run, wants **root** access, just bring up the **Terminal** window and retype the commands.

For me I think sudo just simulates or uses **root** account, for that **execution** only, preventing further damages to the system, something like **Administrator** in XP. Right?

What does **sundo** means?

And please make Ubuntu much friendlier, like a normal and average user won't be able to solve it, me I solved it with many research and of course, sitting all day in front of the PC exploring Ubuntu for more than 15 hours.:lolflag:

**Please explain what is the meaning of the above code.**

---

### Post by taurus on 2008-02-09
The reason you wasted 15 hours because you did things that you were not supposed to, adding yourself to group root!  If you are the first user, the one that you created during the installing process, you already have root privilege so no need to add anything else to your group.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by karlo on 2008-02-09
> **taurus said:**
> The reason you wasted 15 hours because you did things that you were not supposed to, adding yourself to group root!  If you are the first user, the one that you created during the installing process, you already have root privilege so no need to add anything else to your group.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I thought that I am not a member of **root** because when installing or accessing some files, I always see *you must be root* or **permission denied**, obviously you'll think that you are not an administrator.

[SIZE=1]*I think the Users and Groups of Ubuntu are similar to Windows XP's Group Policy... Ubuntu and XP have some similarities, which makes it a little less hassle to be familiar with linux and probably to master/to be and expert with it. The only difference is, when you want a program, you should compile it...*[/SIZE]:lolflag:

By the way, is there a compiler, which is optimized for my processor? *check my signature*.

Also, what's the most **stable** and **longest** *Ubuntu Linux* PC, running, I mean, how long? 1 week?:)

---

### Post by bvanpelt on 2008-02-11
My Feisty server has been running since about October 2007...

---

### Post by newlinux on 2008-02-11
The uptime of 2 of my ubuntu servers is over 120 days. I took them down when I added and/or changed parts (new disk, PCI cards, etc). Before that they were up close to a year. These are edgy servers.

---

### Post by newlinux on 2008-02-11
And there is very little that needs compiling in linux, especially in ubuntu...

---

### Post by karlo on 2008-02-12
> **newlinux said:**
> And there is very little that needs compiling in linux, especially in ubuntu...

Sorry, can you please explain?:confused:

---

### Post by taurus on 2008-02-12
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by karlo on 2008-02-12
> **taurus said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I mean what is the meaning of compiling linux etc... I mean does that person who ran servers, needed to modify the linux kernel just to make it stable?

---

### Post by taurus on 2008-02-12
Compiling usually means you download the source for an app and build it, compiling it, for your machine.  And no, no need to rebuild kernel if you are running a server because the one that you have should be secured and stable.

---

### Post by karlo on 2008-02-12
> **taurus said:**
> Compiling usually means you download the source for an app and build it, compiling it, for your machine.  And no, no need to rebuild kernel if you are running a server because the one that you have should be secured and stable.

What about, me, home user, is i686 version of ubuntu available? And have you tried the latest kernel that is being distributed via updates?

---

