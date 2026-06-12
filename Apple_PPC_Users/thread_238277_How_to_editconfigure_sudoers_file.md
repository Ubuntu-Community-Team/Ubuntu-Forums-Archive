---
title: "How to edit/configure sudoers file"
date: 2006-08-17
forum: Apple PPC Users
---

### Post by spinz8 on 2006-08-17
Hi all,
I think my sudo privilege is broken. After creating a second standard account and selected it as Admin account and remove the default First account admin privelege, i am now unable to sudo.
Please help.
Thanks.

---

### Post by gerbman on 2006-08-17
> **spinz8 said:**
> Hi all,
I think my sudo privilege is broken. After creating a second standard account and selected it as Admin account and remove the default First account admin privelege, i am now unable to sudo.
Please help.
Thanks.Make sure that the account you wish to sudo from is in the 'admin' group. If it is in the 'admin' group and you still cannot sudo, post the contents of /etc/sudoers as well as the output of the 'groups' command.

---

### Post by spinz8 on 2006-08-17
I can only post contents of the etc/group below. Please note that i have replaced the original names with :
aaa>the default admin account
bbb> second account which i hv checked as the Admin after unchecking aaa privilege as admin
I get this dialog:
( "Couldn't display "/etc/sudoers")
("Couldn't display "et/passwd")
There are 3 files group/gshadow/gshaow with crosssed emblem
Regardless of the accounts, i still cant' sudo.
Here are the /etc/group output:
root:0:
daemon:1:
bin:2:
sys:3:
adm:4:aaa,bbb
tty:5:
disk:6:
lp:7:cupsys
mail:8:
news:9:
uucp:10:
man:12:
proxy:13:
kmem:15:
dialout:20:aaa,bbb,cupsys
fax:21:aaa,bbb
voice:22:
cdrom:24:aaa,bbb
floppy:25:aaa,bbb
tape:26:bbb
sudo:27:
audio:29:aaa,bbb
dip:30:aaa,bbb
www-data:33:
backup:34:
operator:37:
list:38:
irc:39:
src:40:
gnats:41:
shadow:42:
utmp:43:
video:44:aaa,bbb
sasl:45:
plugdev:46:aaa,bbb
staff:50:
games:60:
users:100:
nogroup:65534:
dhcp:101:
syslog:102:
klog:103:
aaa\:1000:
lpadmin:104:aaa,bbb
scanner:105:aaa,bbb,cupsys
admin:106:
crontab:107:
ssh:108:
slocate:109:
messagebus:110:
hal:111:
saned:112:
gdm:113:
haldaemon:114:
bbb:1001:

---

### Post by gerbman on 2006-08-17
Since you can't sudo you will need to log in as root to look at the /etc/sudoers file. Do that and post back with your sudoers file.

One problem is the fact that no user accounts are listed under the "admin" group. By default, members of the admin group are allowed to sudo. To add yourself to the admin group, do```
sudo adduser user admin
```where user is the account you want to be able to sudo from.

---

### Post by spinz8 on 2006-08-18
I am afraid i am stuck here. I can't enable the root account. I have read the docs and threads pertaining to this topic. 
I'll have a look again this weekend. Appreciate  further inputs.
Thanks.

---

### Post by scxtt on 2006-08-18
you don't have to enable the root account, just boot into recovery mode - bam - root privileges  ...

---

### Post by spinz8 on 2006-08-18
[quote=scxtt]just boot into recovery mode [/quote]
How do i boot up in recovery mode in osx and what items i need to edit to resuscitate my sudo privilege? Thanks

---

### Post by scxtt on 2006-08-18
OSX?  What? -- why are you asking about OSX on an Ubuntu forum (and yes, i know OSX is "UNIX-based" and we're in the mac section) ...

---

### Post by spinz8 on 2006-08-18
Hi scxtt,
Ok let me rephrase the question:
When the yaboot loader screen shows up, How do i go into recovery mode? or is  there a command in terminal to do so?
Thanks.

---

### Post by gerbman on 2006-08-18
Can you boot into the Ubuntu LiveCD, mount your partitions, and edit the /etc/sudoers and /etc/group file from there?

---

### Post by spinz8 on 2006-08-18
Hi gerbman,
Thanks for really trying to help. Truly appreciate your gestures.
I installed Breezy Badger using the shipit cd and then upgrade it to Dapper via update manager. All went well until i started changing admin/standard account privileges.
I don't hv Dapper live cd and if this is needed then i'll have to download and burn the iso. I am not sure if BB live cd will work as suggested.
Thanks again.

---

### Post by gerbman on 2006-08-18
> **spinz8 said:**
> Hi gerbman,
Thanks for really trying to help. Truly appreciate your gestures.
I installed Breezy Badger using the shipit cd and then upgrade it to Dapper via update manager. All went well until i started changing admin/standard account privileges.
I don't hv Dapper live cd and if this is needed then i'll have to download and burn the iso. I am not sure if BB live cd will work as suggested.
Thanks again.You should be able to mount your Ubuntu partition from the Breezy LiveCD and gain access to the files mentioned. If you have any trouble just post here.

---

### Post by scxtt on 2006-08-18
you should have lines in your boot config (each is different, and i don't know anything about "yaboot") that allows you to boot into recovery mode, for grub they are:
```
[FONT="Courier New"]title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-26-686
boot[/FONT]
```w/ a bit of variation based on your kernel and HDD(s) ...

---

### Post by avtolle on 2006-08-18
To the best of my knowledge, there is no recovery mode boot option (at least a direct option) in Yaboot. So, you will need to boot from your BB live CD, then get to a terminal after it loads, and edit the files gerbman pointed out from there. IIRC, from the BB "Live" CD, you are in root; someone else please correct me if I'm wrong. If not, you will need to type sudo before editing. HTH.

---

### Post by spinz8 on 2006-08-20
[I]Hi, thanks for all the responses so far,
I have booted from BB liveCD. i still can't sudo to add myself to the admin.  Perhaps i didnt do the correct way.  How do i mount  livecd to  installed  ubuntu partition? 
[/I]

---

### Post by gerbman on 2006-08-20
> **spinz8 said:**
> [I]Hi, thanks for all the responses so far,
I have booted from BB liveCD. i still can't sudo to add myself to the admin.  Perhaps i didnt do the correct way.  How do i mount  livecd to  installed  ubuntu partition? 
[/I]Once you boot into the LiveCD, you need to first mount your Ubuntu partition(s) to gain access to the files. Get a list of your Ubuntu partitions by firing up GParted ("sudo gparted" from a terminal). You need to get the device (e.g., /dev/sda1) for the root partition in your Ubuntu system. Mine is /dev/sda3, so I'll use that in my post. Create a directory to mount the partition to in your home directory:```
mkdir ~/root
```and mount the root Ubuntu partition:```
sudo mount -t ext3 /dev/sda3 ~/root
```Now you should be able to edit the 'sudoers' and 'group' file with```
sudo gedit ~/root/etc/sudoers
```and```
sudo gedit ~/root/etc/group
```respectively. If you're not sure how to edit them, just post their contents and we'll try to help.

---

### Post by spinz8 on 2006-08-21
Hi gerbman,

Thanks for the reply.

Before you posted this reply, i spent quite sometime with the LiveCd. This was what i discovered. There is indeed a "rescue" (recovery] mode  on the yaboot loader. I was presented with 03 column of choices:

1. rescue-powerpc / live-powerpc /live-expert

2. rescue / live / live-powerpc64

3. rescue-powerpc64 / live-expert-powerpc / live-expert-powerpc64

I opted for number 1 which was suitable for my hardware (iBook G4) and then there were friendly walk-throughs of installing Ubuntu like Language>Location>Keyboard and then full hardware detection until it came to the partition part asking me to mount the root file. I was dumbstruck as i couldn't remember my root partition. So i barged through each partition like /dev/discs/disc0/part 1-13 Any failed mount, it will state the status. It was like a gamble. At last i managed to mount the root file partition which gave  shell command.I typed few simple command lines and it worked.

I tried your suggested command**sudo addmysusername user admin** but it wont accept. So i tried this command

```
 addgroup myusername admin
``` I quickly checked etc/group file and indeed i have regained my admin privileges :-D  All the missing menu lists:system>administration are back and so is the application>Add/remove menu list.  I will look at sudoers file again to edit once i recovered from jetlag.
I am happy that i can sudo again and thus the important updates.
Thanks to everyone who responded to this thread especially gerbman and avtolle for their resourceful tips.
Kind regards.

---

### Post by gerbman on 2006-08-21
Cool, glad to see something is working again :)

---

### Post by avtolle on 2006-08-21
I echo gerbman's comments.

---

### Post by xKid on 2006-10-10
how i add the domain group in the sudoers ?

only the domain user do work without problems...


sorry english :-|

---

