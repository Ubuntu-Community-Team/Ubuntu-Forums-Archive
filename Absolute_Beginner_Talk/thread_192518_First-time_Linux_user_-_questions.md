---
title: "First-time Linux user - questions"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Azhrei on 2006-06-08
Hi everyone.

I've just installed version 5.10 of Ubuntu, dual-booting with WindowsXP Professional. I gave it a small 3GB partition for itself, with the express intent of using it for 'net browsing and nowt else. I really like the interface and all, but I'm having problems trying to access my hard drives, and getting the damned thing onto the 'net. It comes with Firefox and Gaim pre-installed so that's me pretty much set up, apart from the fact that I can't connect just yet.

I've no idea how to set up my dial-up connection, and though I tried with the Terminal er... thingy, it didn't save my password which I don't want to have to type in each time (it's very random, decided by my ISP obviousleh). I tried that sudo pppoeconf thing in the Terminal that someone suggested somewhere else on the forums, but though it detected my network card (which I don't want it to do anything with) it said there was another pppoe conflicting.... or something.

Also, about my drives... it won't let me access them, saying that they are not owned by me and therefore I cannot set the permissions- they're there on the desktop, but the only way to access them is by going to Administration and clicking on Disks, then clicking on Partition and Browse. I can't copy anything over because of this permissions thing, and likely also because they are all NTFS formatted. I have a 20GB drive for Windows (3GB of which now has gone to Ubuntu), a 120GB internal Seagate Barracuda, and an external 120GB Western Digital.

I know I've given Ubuntu little space on the drive to do anything, but all I want to use it for is browsing the 'net. So far I like the interface (having used nothing but Windows for years) but all this network stuff that keeps cropping up whenever I flit around the settings searching in vain for any dial-up or *any* Internet connection setup is driving me crazy... and to me is user-unfriendly. Also, the drives thing is annoying me. I know that writing to NTFS drives is unsupported (or at least, experimental) at this time but all I'd like to do is *access* the files. I'd like to play music from my mp3 collection that is over 10GB in size and resides on my portable drive.

I do not want to reformat these drives or change them to FAT32 or anything... I use Windows for nearly everything and being a big gamer, it is important. Can anyone help me?

---

### Post by nalmeth on 2006-06-08
Here's a howto for modems in Ubuntu:
[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

You should really allow a little bit more for ubuntu, eventually you're going to want to save something off the net, and when you fill up your home folder, you're not going to be able to log in. You have a total of 240 gigs of unused space?

Also, Dapper Drake is officially stable, if you can access high-speed + CD-burner you might like to change install that.

Alternatively you can upgrade when you get your dial-up going. It will be slow though.

ABout the NTFS drives, can you post the output of this command in the terminal?

cat /etc/fstab

With help from the forums here, hopefully you'll be to the point where you're *only* using windows for gaming. One step at a time though

---

### Post by u.b.u.n.t.u on 2006-06-08
Hi,

"I've just installed version 5.10 of Ubuntu". The latest version is Dapper and I for one recommend it over 5.10.

Dapper has many new features so it may be worthwhile installing that version instead of a previous version which has less work done to it.

There are 2 "versions" of Dapper.

Desktop "live CD which will put an install icon on the desktop"

and

Alternative which is an OEM and standalone install ("text", but actually displays a gui).

You will find a lot to "update" with 5.10, many fixes.

---

### Post by Azhrei on 2006-06-08
Thanks for your replies.

Nalmeth - I looked at that page once and I wanted to see if someone could help me without my having to print it out and then read all of it to try and get my connection to work (it's very long...). I'll give it a try, though.

I have no idea what Dapper Drake is. I'm a complete newbie when it comes to Linux and Ubuntu.

I can't post the output of the drives because I have no way to get anything from Linux onto my drives. I guess I could write the thing down and type it out here...


U.b.u.n.t.u - Version 5.10 was the cd I picked up out of curiousity in a computer shop the other day. I have dial-up internet only and cannot download any updates - and even if I did, I can't transfer them onto my Linux partition because I cannot get Linux to access my hard drives.

---

### Post by u.b.u.n.t.u on 2006-06-08
"I have no idea what Dapper Drake is."

My analogy is, you installed "Windows 98SE" instead of "Windows XP Pro".

The latest version of ubuntu is "Dapper Drake 6.06", released 1 June 2006. That is what you want to install.

Your or an ISP you have access to may provide a free download list and ubuntu may be there so it doesn't count towards your quota. You may want to check that out if you haven't already.

edit:

You can order free CDs of ubuntu:

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

I never used 5.10, only 6.06 so I can't really give you any advise about that version.

---

### Post by jrd on 2006-06-08
Go to "system tools" (I think, I use Kde so i'm not sure) and click the terminal icon. When it comes up type "cat /etc/fstab" and post what it says. (this is what nalmeth was reffering to) Then maby we can fix your drive problem.

---

### Post by Azhrei on 2006-06-08
Will do, JRD.

And thanks for the information, u.b.u.n.t.u.

---

### Post by AaronThorpe on 2006-06-08
Well Hey Im a real noob, but I just downloaded an SMS service and have no freakin clue how to install it.....help please

---

### Post by nalmeth on 2006-06-08
Sorry, I should have explained better. 

Dapper Drake is just the code name for the newest release of ubuntu. Breezy Badger was the previous release (5.10)

Also, I sympathize with you, that the howto is a little long.

A couple questions before you try to do it. 

Do you have a floppy drive and disk you can use? If not, to get the scanmodem program over to ubuntu you'll need to get a driver for windows to write to ext3 (ubuntu's filesystem).

Is there a way you can acquire the Dapper Drake install CD? Because if you want to upgrade after setting the modem up, you'll have to redo part of the driver setup for dapper. 

Also, that command was for you to type in Ubuntu, /etc/fstab shows you how the drives are setup, you can change the user permission of the drives through this file. You can worry about that after the modem is setup.

EDIT: @ AaronThorpe
You should start your own thread for you problem.

---

### Post by Azhrei on 2006-06-08
The cat/etc/fstab command did not work. The Terminal responds with a "file or folder not found".

I've also been trying to setup drivers for my Lucent winmodem, but the FAQ is either wrong or I'm screwing up - Linux will not let me create a new file in the /etc/udev/rules.d/ folder called 10-local.rules. I tried opening up another file in there, erasing everything and typing in - 

#ltmodem
KERNEL="ttyLTM0", SYMLINK="modem"

But it refused to save as 10-local.rules (I didn't delete the other file). Seems I don't have permissions for that folder, either.

---

### Post by jrd on 2006-06-08
Note the difference:
cat /etc/fstab (correct)
cat/etc/fstab (incorrect)
 Try it again and let us know.

---

### Post by Azhrei on 2006-06-08
Damn me... be right back.

---

### Post by jrd on 2006-06-08
To get permission to edit the file pull up the terminal and type "sudo nautilus" then brows to the file as normal. [COLOR="Red"]SUDO GIVES YOU ROOT PERMISSIONS SO BE CAREFULL!!![COLOR="Red"][COLOR="Black"][/COLOR][/COLOR][/COLOR]

---

### Post by Azhrei on 2006-06-08
Here are the results - 

<fs>           <mp>          <type>     <opt>                             <dum> <pas>

/dev/hda2    /                  ext3        defaults                              0      0
/dev/hda1   /media/hda1    ntfs        defaults,errors=remount -10    0      1
/dev/hdb1  /media/hdba1   ntfs        defaults                               0      0
/dev/sda1  /media/sda1     ntfs        defaults                               0      0 
/dev/hdc   /media/cdrom0  udf,iso9660,users,noauto,                    0       0
/dev/hdd   /media/cdrom1  udf,iso9660,users,noauto,                    0       0


Sorry that it's all uneven and whatever. Also, I'm really tired, so I just did my best copying them onto paper.

Edit - I edited them so that there are proper spaces, but the forum won't put them in there. Sorry.

---

### Post by Azhrei on 2006-06-08
*Hopeful bump* 


>_>

---

### Post by jrd on 2006-06-10
Add this to all ntfs mounts in fstab. uid=1000,gid=0,auto,rw,users (assuming your user id is 1000)

---

