---
title: "Putting /home on a seperate partition"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Torquemada28 on 2006-06-20
After reading a few threads here, I concluded that putting the /home directory onto a seperate partition is a wise course of action.
I've partitioned 16Gb in which to store /home.

Now a couple of questions.

1) How do I get it to mount? What do I have to change in fstab?

2) How do I get Ubuntu to see the new partition as /home? What file will I have to edit/configure?

As this is a fantastic community, I know that someone will give me lovely, concise answers that won't cause my noob cranium to implode.
That's what I'm hoping, anyway.

---

### Post by xXx 0wn3d xXx on 2006-06-20
[QUOTE=Torquemada28]After reading a few threads here, I concluded that putting the /home directory onto a seperate partition is a wise course of action.
I've partitioned 16Gb in which to store /home.

Now a couple of questions.

1) How do I get it to mount? What do I have to change in fstab?

2) How do I get Ubuntu to see the new partition as /home? What file will I have to edit/configure?

As this is a fantastic community, I know that someone will give me lovely, concise answers that won't cause my noob cranium to implode.
That's what I'm hoping, anyway.[/QUOTE]
Ubuntu will automaticlly mount it. You should not have to edit anything.

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=xXx 0wn3d xXx]Ubuntu will automaticlly mount it. You should not have to edit anything.[/QUOTE]

```
mount: can't find hda5 in /etc/fstab or /etc/mtab
```

The only thing Ubuntu is automatically mounting is me.
My *** is getting sore so let's try something else.;)

---

### Post by taurus on 2006-06-20
Edit your /etc/fstab and add the following line to it!!!
```

/dev/hda5  /home  ext3  defaults  0  2

```
Then mount it with
```

sudo mount -a

```

---

### Post by mishranurag on 2006-06-20
Did you partition the /home while installing? I have done that couple of times and UBUNTU always mounted those partitions. UBUNTU also mounted other drives as well. 

Could you elaborate on how you mae partition for /home?

---

### Post by bollix47 on 2006-06-20
Take a look [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") for some info re what you're trying to do.

---

### Post by ????? on 2006-06-20
[Here's](http://www.psychocats.net/ubuntu/separatehome.html) another good resource

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=taurus]Edit your /etc/fstab and add the following line to it!!!
```

/dev/hda5  /home  ext3  defaults  0  2

```
Then mount it with
```

sudo mount -a

```[/QUOTE]

[sarcasm]Thanks for that.[/sarcasm]
Now when I try to open a konsole I get...
Service '/home/brad/.kde/share/apps/kicker/konsole.desktop' is malformatted.
Maybe you'd like to tell me how to undo the damage without a konsole window.

[QUOTE=mishranurag]Did you partition the /home while installing? I have done that couple of times and UBUNTU always mounted those partitions. UBUNTU also mounted other drives as well. 

Could you elaborate on how you mae partition for /home?[/QUOTE]
When I installed, I had one large partition for / and one small one for /swap.
Those in the know have suggested that it's a good idea to put /home on it's own partition, so I took 16Gb from the large partition to make the extra partition for /home. This new partition is formatted but contains no files because it wasn't mounted, otherwise I would've copied to contents of /home to it.
I suspect that Ubuntu doesn't automatically mount the new partition because it wasn't made when Ubuntu was installed, therefore it isn't in fstab.

[QUOTE=bollix47]Take a look [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") for some info re what you're trying to do.[/QUOTE]
That looks like exactly what I was after. Thanks.
I'll follow those instructions just as soon as I fix my brand new problem.
*glares at taurus*

---

### Post by Irony on 2006-06-20
This is how I moved my home partition from the root partition to hda7;

First boot up as normal into Ubuntu;

[http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[PHP]sudo mkfs.ext3 /dev/hda7
sudo mkdir /mnt/hda7_Home
sudo mount /dev/hda7 /hda7_Home[/PHP]

Now go to single user mode (text screen) using the init command;

[PHP]sudo init 1 (wait, wait, wait... until prompt root@ubuntu:~#)
cd /home
cp -ax * /hda7_Home
cd /
mv /home /home_old
mkdir /home
mount /dev/hda7 /home
init 2  (or Ctrl D)[/PHP]

Now I'm back in graphical mode;

[PHP]sudo gedit /etc/fstab[/PHP]

Add;

[PHP]/dev/hda7   /home   ext3   defaults   1   2[/PHP]

---

### Post by Torquemada28 on 2006-06-20
> **Irony]This is how I moved my home partition from the root partition to hda7 said:**
> http://www.gentoo.org/doc/en/articles/partitioning-p1.xml[/url]

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[PHP]sudo mkfs.ext3 /dev/hda7
sudo mkdir /mnt/hda7_Home
sudo mount /dev/hda7 /hda7_Home[/PHP]

Now go to single user mode (text screen) using the init command;

[PHP]sudo init 1 (wait, wait, wait... until prompt root@ubuntu:~#)
cd /home
cp -ax * /hda7_Home
cd /
mv /home /home_old
mkdir /home
mount /dev/hda7 /home
init 2  (or Ctrl D)[/PHP]

Now I'm back in graphical mode;

[PHP]sudo gedit /etc/fstab[/PHP]

Add;

[PHP]/dev/hda7   /home   ext3   defaults   1   2[/PHP]

Thanks for the info but without a konsole (read my previous post), it's of little use to me.

---

### Post by Torquemada28 on 2006-06-20
OK, I have very limited knowledge of linux but the only way I can see to fix fstab is to boot into recovery mode and use...
```
nano /etc/fstab
```

I can then (hopefully) remove the last line I entered and save it.

Will this work or is there something I'm not aware of?

---

### Post by caldaar on 2006-06-20
I am new to linux as well, so take this advice with newbie in mind and think it through.  The error that you are getting is that the '/home/brad/.kde/share/apps/kicker/konsole.desktop' is malformatted.  

Would it make sense to setup the format using the "mkfs -t ext3" command from the recovery, then cp the /home to the new partition?

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=caldaar]I am new to linux as well, so take this advice with newbie in mind and think it through.  The error that you are getting is that the '/home/brad/.kde/share/apps/kicker/konsole.desktop' is malformatted.  

Would it make sense to setup the format using the "mkfs -t ext3" command from the recovery, then cp the /home to the new partition?[/QUOTE]

Maybe, maybe not.
The problem I have is that if that doesn't work, I have a feeling that Ubuntu will be unbootable and I'll be right royally f*cked.
What I really need is a fool-proof way of editing the fstab from recovery mode.
I can then delete the last (erroneous) line, boot as per normal and follow the instructions posted by bollix47.

---

### Post by caldaar on 2006-06-20
Tell you what,  I have a spare workstation here...  I am going to try to recreate the issue and see if it will work....  it may take a little bit.

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=caldaar]Tell you what,  I have a spare workstation here...  I am going to try to recreate the issue and see if it will work....[/QUOTE]
Much appreciated.
The experts sure picked a lousy time to go silent on me. 
[QUOTE=caldaar]  it may take a little bit.[/QUOTE]
I'm not going anywhere.
I have to fix this before I do anything else.
Which is a pain, since it's 2am here and I want to go to bed. :(

---

### Post by caldaar on 2006-06-20
Not a problem..  I understand the frustration.... looking through the thread, the experts gave you exactly what you asked for assuming that you had all ready setup the file system and copied the files.... I believe those are the only steps that are missed, but I should be able to give deffinate steps shortly.

A couple of questions:

when you made the partition... do you know what HDA it is labeled as?  

Did you format the partition?  If yes, what file system?

---

### Post by Torquemada28 on 2006-06-20
Success!
*does happy dance*

I used Ctrl+Alt+F1 to get a console and
sudo nano /etc/fstab
to edit my problematic fstab.
Rebooted and everything is fine again.
*does happy dance again*

I think I'll leave the original problem until tomorrow.
Thanks for your assistance caldaar. :)
*edit*
[QUOTE=caldaar]
A couple of questions:

when you made the partition... do you know what HDA it is labeled as?  

Did you format the partition?  If yes, what file system?[/QUOTE]
The partition is hda5 and it's formatted as ext3.

---

### Post by caldaar on 2006-06-20
ok, have a good night....

---

### Post by juicybananahead on 2006-06-20
[QUOTE=Torquemada28]Thanks for the info but without a konsole (read my previous post), it's of little use to me.[/QUOTE]
You should be able to use the command line by pressing Ctrl + Alt + F1. Ctrl + Alt + F7 brings you back to your X session.

Edit: Whoops, redundant comment.

---

