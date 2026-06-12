---
title: "fsck not running any longer"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by mblind on 2008-02-08
Hi there,
 My fsck no longer runs.. it should be checking my drive every 30 times but I have boot well over 90 and it never runs.. that is it's not anymore, it use to.. But now it has stopped working.

How can i re-enable it?
I did run
 sudo tune2fs -l /dev/sda1

And I can see that it should be running every 30 times but it never does.

Also, I have run sudo tune2fs -c 30 /dev/sda1
and I have changed the number to 3  and it still doesn't help..  what can I do to bring this back.. I am kinda of new to linux and need some help..

Thanks.

---

### Post by talsemgeest on 2008-02-08
[http://ubuntuforums.org/showthread.php?t=99662](http://ubuntuforums.org/showthread.php?t=99662)

Hope this helps :)

---

### Post by talsemgeest on 2008-02-08
Even better, try this: [http://packages.ubuntu.com/gutsy/utils/showfsck](http://packages.ubuntu.com/gutsy/utils/showfsck)

---

### Post by mblind on 2008-02-08
How the heck do you install showfsck..?? Ahh.. I figured it out

**Install showfsck in Ubuntu**

sudo apt-get install showfsck

This will complete the installation

Using showfsck

If you want to see the number of reboots before next forced fsck using the following command (Terminal)

sudo showfsck

output looks similar to the following

15/30 mount(s) until fsck for /dev/disk/by-uuid/edadb298-aae6-4549-b5dc-55c6184fdbc4

---

### Post by bobbocanfly on 2008-02-08
> **mblind said:**
> How the heck do you install showfsck..??

At a terminal type ```
sudo apt-get install showfsck
```. Once you have done this in the same terminal session type ```
sudo showfsck
``` and post the output here.

---

### Post by mblind on 2008-02-10
Ok.. I have showfsck running just fine.. Now the system goes through 30 boots and it still doesn't ever run fsck. 

This is so odd. Can anyone help with this weird problem..

---

### Post by talsemgeest on 2008-02-11
Can you try forcing a check?

---

### Post by mblind on 2008-02-12
If I boot to a Live CD then manually type fsck /dev/sda1 it works.. 

How do I force a fsck?

Also showfsck now shows
*-3*  /30 mount(s)  until fsck for ... etc etc. (Yes that is a negative 3)

I have also used tune2fls and changed settings to a lower number.. still nothing.. ugh.. any ideas?

---

### Post by talsemgeest on 2008-02-12
I came across a program a couple of weeks ago. Ill see if I can dig it up.

---

### Post by talsemgeest on 2008-02-12
Oh, its even easier than I thought!
Just do this: [http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by Herman on 2008-02-12
[                   'Forcing' (an early) filesystem check]("http://users.bigpond.net.au/hermanzone/p10.htm#Forcing_a_filesystem_check")

Regards, Herman :)

---

### Post by mblind on 2008-02-13
Ok here is what I did.
Login as the root:
$ su -
Change directory to root (/) directory:
# cd /
Create a file called forcefsck:
# touch /forcefsck
Now reboot the system:
# reboot

system reboot.. Still No Fsck.. ahhhhhhhhhhh. what the heck!! What now?

---

### Post by Herman on 2008-02-13
Just typing '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]sudo touch /forcefsck' should have been sufficient
[/FONT][/COLOR]```
sudo touch /forcefsck
```Do you have some other partition with a file system in it or a USB flash memory stick you can unmount and run fsck on to see if fsck works?
The command fsck normally runs is fsck -C -R -A -a[SIZE=-1][COLOR=Sienna][/COLOR][/SIZE]```
sudo fsck -C -R -A -a /dev/sdx,y
```Where: '/dev/sdx,y' is replaced with some hard disk and partition number, preferably with an ext3 file system if possible.

You can always run a file system check from your Ubuntu Live CD or from a GParted LiveCD now and again, that will do a good file system check for you, but you'll need to remember to run it now and again yourself. Maybe that will help you keep it running well until it's time to install Hardy Herron, which won't be for around a couple of months from now at least. Here's how to run your own file system checks, 

[                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user friendly GUI method

[                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line

Regards, Herman :)

---

### Post by erginemr on 2008-02-13
Following this thread:
[http://ubuntuforums.org/archive/index.php/t-300477.html](http://ubuntuforums.org/archive/index.php/t-300477.html)

Trivial it may be, but I believe you have also checked your /etc/fstab file that the filesystem check flags on your corresponding Linux drives are open.

---

### Post by Herman on 2008-02-13
> Trivial it may be, but I believe you have also checked your /etc/fstab file that the filesystem check flags on your corresponding Linux drives are open. AHA! Good point, erginemr ! Thanks. Why didn't I think of that? That might solve mblind's problem.   :)

---

### Post by mblind on 2008-02-13
Sorry I am a little confused now.. So do I need to change something in my fstab? here is what mine looks like currently (Also, Thanks so much for all this help.. I think we are really close to solving this now.)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0baa3442-9435-4aaa-9f38-f057f5d81f0a /               ext3    defaults,errors=remount-ro 0       0
# /dev/sda5
UUID=5daee7e4-994a-4a33-b656-93e57670da8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Herman on 2008-02-13
> Sorry I am a little confused now.. So do I need to change something in my fstab? here is what mine looks like currently (Also, Thanks so much for all this help.. I think we are really close to solving this now.) Oaky, thanks to erginemr's input mainly. :)

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0baa3442-9435-4aaa-9f38-f057f5d81f0a /   ext3    defaults,errors=remount-ro 0    [COLOR=Sienna]**1**[/COLOR]
# /dev/sda5
UUID=5daee7e4-994a-4a33-b656-93e57670da8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```See what I changed? I changed the '0' to a '1' in the 'pass' column for the / (root) of your Ubuntu partition.

That should solve your problem, again, mainly thanks to erginemr for suggesting that. 

Regards ,Herman  :)

---

### Post by mblind on 2008-02-13
FIXED!!!!!!! Hurray.. Thank you both soooo much.. These Ubuntu Forums are really amazing.. Thanks again for all your time and trouble!!

Herman and erginemr  you are the best.. thanks again!!

---

### Post by Herman on 2008-02-13
:)  Okay!  Happy Ubuntuing! 
Regards, Herman  ):P

---

### Post by talsemgeest on 2008-02-13
Well, I would never have thought of that. Glad you have it fixed!

---

### Post by erginemr on 2008-02-14
**talsemgesst** -> Glad that your problem has been solved. Could you please mark your thread as SOLVED form the "thread tools" menu above? Take Care & Keep up the good work!

**Herman** -> Our paths did not cross in any previous thread but I have always enjoyed reading your former posts and learned a lot of things from them. And from your following excellent wiki:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

which should be on the to-do list of all linux newcomers and experienced users alike.

What strikes me even more is your positive attitude and politeness coupled with your lore, which is few and far between among experienced Linux users (aka geeks). I have always admired your approach and in my opinion, you are a great asset to the Ubuntu Community. So, a big **thank you** on my behalf.

Take Care,

Emrah

---

