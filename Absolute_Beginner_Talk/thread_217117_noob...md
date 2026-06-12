---
title: "noob.."
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by nightwolf2k5 on 2006-07-16
ok.. i just installed ubuntu.. never used linux in my life and suddenly just decided to see how it will be.. well.. after a whole hour of figuring out how to install ubuntu.. i finally managed to do it.. but.. my modem does not work.. i downloaded some linux drivers but they are like stored in the windows partitition.. which incidentaly i cant access..
anyways.. i kinda was scannin through the forum and saw some of the similar problems faced by others.. the solution to which... was some sorta code..
i got 2 quiries..
1. where on earth do u type the code?
2. is there like an easier way to get my modem to work?

btw.. its an billion 7000 adsl modem..

---

### Post by Jagot on 2006-07-16
1)
Applications -> Accessories -> Terminal

2)
What modem do you have?

---

### Post by nightwolf2k5 on 2006-07-17
got an adsl modem.. billion 7000... i need the drivers man.. i cant quite connect otherwise.. right?
and.. how do i view the files in the other partitions? like ntfs.. i keep gettin some weird message of some mounting thingy ](*,) 
oh yeah.. and even mp3's don work :( and since i cant go online.. its like.. it compounds the problems since i kinda go online and maybe download other codecs and stuff.. so.. i'm lookin to like figure a way to go online first..

---

### Post by Sonic Alpha on 2006-07-17
USB modems can be a bit of a pain to get working.  You may have to get a ADSL modem/router. :(

---

### Post by nightwolf2k5 on 2006-07-17
oh man!! don tell me.. lets see.. i did download some linux drivers for my modem.. but.. its like its in the ntfs portion.. anyway i can access that through ubuntu?
i mean.. all i want is like to do most of what i do in windows in ubuntu.. and use windows just for like games and now.. maybe for surfing.. but.. i don mind getin my hands dirty to get my modem to work.. that way i guess i'll even learn a few things abt linux.. i guess..

---

### Post by Sonic Alpha on 2006-07-17
You should be able to read the contents of the NTFS drive.  You won't, however, be able to write to that drive.

If you can't get access, there is a nice tutorial on mounting drives, [here]("http://www.psychocats.net/ubuntu/mountwindows.php").

And yes, it is a pain to get an USB ADSL modem working (well, **SOME** of them anyway, lol).  I had a nightmare trying to get mine to work, but that's more my ISP's fault for giving me a rubbish modem ;)

---

### Post by hanexar on 2006-07-17
If you use your internet connection with a username and password, try to configure it with this line:

```
 pppoeconf 
```

---

### Post by nightwolf2k5 on 2006-07-17
configure it with that line?? how'd i do that..
i mean.. what are the things i'll need to do.. i dunno anythin u c!!:( 
i'll try that mounting thing.. btw.. i don have write permission even on my linux drives!! its like while installin ubuntu.. it refused to install on the partitions i created for it.. so i just deleted the partions and then chose the "install on largest free space option".. so.. i guess i'll need write permission to install anythin right?
](*,)

---

### Post by nightwolf2k5 on 2006-07-17
@sonic..
dude.. thanks a lot for that tutorial.. but.. it does not work.. :(
it gives an error sayin only the root can mount sda6 or somethin like that.. crap man..

---

### Post by givré on 2006-07-17
Have a look there guys,
[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

EDIT: And if you want full write support on your NTFS partition, and are not  affraid by beta product, have a look there : [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by Spinelli on 2006-07-17
> **nightwolf2k5 said:**
> @sonic..
dude.. thanks a lot for that tutorial.. but.. it does not work.. :(
it gives an error sayin only the root can mount sda6 or somethin like that.. crap man..

Read this page if you are having problems with root permissions ....

[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29")

---

### Post by nightwolf2k5 on 2006-07-17
dude.. as far as i've understood the link u gave me about the root thingy, its like the codes i used when i was doing the whole thing to make the ntf partition to work, well.. it seems that i was using the same codes.. i.e "sudo".. and stuff.. but what it does say is that u should not open graphical programs using sudo..

ok.. i'm a lil confused with this.. now.. what i did after typin the sudo command thing and editing the stuff that was supposed to be edited, was to go to the "my computer" equvalent in ubuntu and double click on the ntfs drive.. but.. then it said it could not be mounted cuz of some only root can mount it..

---

### Post by ProjectGod on 2006-07-17
> **nightwolf2k5 said:**
> dude..
:lol:

[www.psychocats.net](www.psychocats.net)

search for UBUNTU TUTORIALS then MOUNT WINDOWS link on the side bar.

after that we'll get internet working... and if that works we'll get you playing mp3s in no time.

let us know how you go... [SIZE="7"]dude![/SIZE] :lol:

---

### Post by nightwolf2k5 on 2006-07-18
lol!.. guess i'll cut the dude stuff.. anyways
its like this man.. u know the first tutorial i tried.. well.. it was from that site! 
i kinda followed everythin there but.. 
see this..
```
/dev/hda1 /media/hda1 ntfs defaults 0 0
```
well.. i dinhave any like like that... so i kinda created that line.. but since my partitions were called sda.. i changed that..
somehow.. i think that might have been the problem... but.. er.. i dunno.. :D

---

### Post by ProjectGod on 2006-07-18
what kind of disk do you have dude? how many? iDe or ScSI?

create a mount point on your root by:

**sudo mkdir -m 775 /windowsdata**

then open up your /etc/fstab by...

x@y:/$ **sudo nano /etc/fstab**

then include right at the bottom a string simiar to the one below... wont be the same... but i hope you get the picture.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**/dev/hda4       /windowsdata           ntfs    nls=utf8,umask=0222 0 0**

if you've got one hard disk... and you firstly installed windows... then its bound to be /dev/hda1... anyway you'll have to use some spaces between each entry obviously... the above example is to damn crampt.

save it and exit out of nano... then:

x@y:/$ **sudo mount -a**

then you have a nice windows mount. if you don't you probably have a scsi drive... which is simple enough to mount also... just use /dev/sda1

hope this helps out [COLOR="Pink"][SIZE="7"]DUDE[/SIZE][/COLOR]

---

### Post by nightwolf2k5 on 2006-07-18
i got one disk, its a sata disk.. its designated as sda1,2 etc..

the sda1 is where the windows os is present.. ok.. i like added the stirng like in the middle of the whole thing.. i'll add it in the end.. btw.. its like i have 3 ntfs partitions.. do i have to choose the one where windows is mounted or any of the other partitions will also do.. its like i chose some other partition cuz i din wanna risk screwin up the partition with windows in it..
anyways.. i'll try it again and update u.. thanks a lot dude ;)
btw.. will it make a difference if i like go for a linux course or something? the whole fact of not bring able to even like open a folder in linux is like givin me the creeps! just few months back i thought my comp knowledge was quite decent! so.. anyways.. i'll try it.. dude.. can i like msn u or somethin? its like i can probably better understand stuff.. tats if u don mind..

---

### Post by nightwolf2k5 on 2006-07-18
ok dude.. i tried everything again.. somehow.. i get the feelin that somethin is missing big time.. also the fact that i don understand a single code i guess makes it a huge disadvantage cuz even if i made a mistake i would not know!! ](*,) ](*,)

---

### Post by givré on 2006-07-18
Okay guy. We will retake that point by point.

1. You need to know what are your NTFS partition. In a terminal, type:
```
sudo fdisk -l|grep NTFS
```
fdisk -l will list all your partition, and [grep NTFS will restreind the output to only the NTFS partition.

2. Now that you know what are your NTFS partition, you need to create a directory where the partition will be mount point (if it's not already done)
```
sudo mkdir /media/<the name you want>
```
do that for each partition.

3. Last thing, you need to configure /etc/fstab . This file store the partition which will be mount at boot time and and the option how to mount them.
```
sudo gedit /etc/fstab
```
This will look like, if we take the exemple of dude ProjectGod:
```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb3 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```If your windows partition is not there, change it so it will looks like that:
```
/dev/<your partition>   /media/<your mount point>   ntfs   nls=utf8,umask=0222   0   0
```
If there are no line, just add one like the one above.

4. Remount your partition:
```
sudo umount -a
sudo mount -a
```

And that's all. If it doesn't work, try to reboot. If always not, post here your /etc/fstab and the result of sudo fdisk -l 

8)

---

### Post by nightwolf2k5 on 2006-07-18
ok.. i'll try this again.. 
now.. here
>  Now that you know what are your NTFS partition, you need to create a directory where the partition will be mount point (if it's not already done)
```


sudo mkdir /media/<the name you want>

```
do that for each partition.
how do u do that for each partition? do u just put some random name and add them in that /etc/fstab thingy?
after i do this.. when i go into the my computer equvialent in ubuntu.. will those drives open?
anyways.. i'll try it again and let ya'll know!!
thanks man! :)

---

### Post by nightwolf2k5 on 2006-07-18
oh sweet sweet sweet!!! it works!!! whoo!!! finally.. oh man!! i think i kinda understood the whole process.. thanks so much man!! all of ya'll have been really patient!!
now.. to install my modem..
its like a billion 7000 adsl modem (uses the usb!! :( )
but.. when i checked the driver cd, it did have a driver for linux :)
but.. i'm all at sea to figure out a way to install it.. :(
there are some directions.. but.. again.. i need someone to like tell me in "English" what that means! :P
i'll try gettin the directions.. its like in ubuntu.. and i need to restart and like write it down :D
thanks again ppl! i owe ya'll one big time

---

