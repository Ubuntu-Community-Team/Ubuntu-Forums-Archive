---
title: "File permissions disabling ability to launch from system/admin?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by TwinkieFGR on 2008-01-17
I wanted to edit the amount of buttons on my mouse, and I needed permission.
So, I went for the easy way and I ran-
user@host:/home/user$ sudo chmod 777 -R /usr

And it let me edit it.

Then I tried to launch Synaptic to get imwheel, and I couldn't. After a bit of searching I found this
[http://ubuntuforums.org/showthread.php?t=491190](http://ubuntuforums.org/showthread.php?t=491190)

I'm having the exact problem he was, and they mentioned a command line to fix this, but they didn't know what it was.

I really really don't want to have to reinstall, could someone please help me fix this?

---

### Post by dcstar on 2008-01-17
> **TwinkieFGR said:**
> I wanted to edit the amount of buttons on my mouse, and I needed permission.
So, I went for the easy way and I ran-
user@host:/home/user$ sudo chmod 777 -R /usr

And it let me edit it.

Then I tried to launch Synaptic to get imwheel, and I couldn't. After a bit of searching I found this
[http://ubuntuforums.org/showthread.php?t=491190](http://ubuntuforums.org/showthread.php?t=491190)

I'm having the exact problem he was, and they mentioned a command line to fix this, but they didn't know what it was.

I really really don't want to have to reinstall, could someone please help me fix this?

```
sudo chmod 755 -R /usr
```
may work.

---

### Post by TwinkieFGR on 2008-01-17
That tells me this-

sudo: /etc/sudoers is mode 0777, should be 0440

So what do I do here

---

### Post by dcstar on 2008-01-17
> **TwinkieFGR said:**
> That tells me this-

sudo: /etc/sudoers is mode 0777, should be 0440

So what do I do here

I have no idea, you are supposed to be working in /usr, not /etc.

---

### Post by TwinkieFGR on 2008-01-17
I don't know why it said etc, this is exactly what happened after I did what you told me to -

censored-desktop:~$ sudo chmod 755 -R /usr
sudo: /etc/sudoers is mode 0777, should be 0440

---

### Post by ByteJuggler on 2008-01-17
Well the error mesage implies you did not just change the permissions inside /usr to 777, but in /etc as well.  Perhaps you entered 

```
sudo chmod 777 -R / usr
```

instead of 

```
sudo chmod 755 -R /usr
```

Note the missing space.  This would've caused you to make every single file on the filesystem writable and executable by anyone.  (This by the way is a hackers dream and a very bad idea.)

For a start, try to change the permissions on sudoers file back to what it's supposed to be:

```
chmod 440 /etc/sudoers
```

Then see if sudo will work again.

---

### Post by TwinkieFGR on 2008-01-17
I don't think I put a space, but I could be wrong.

I did what you said and got this

censored-desktop:~$ chmod 440 /etc/sudoers
chmod: changing permissions of `/etc/sudoers': Operation not permitted
censored-desktop:~$ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0777, should be 0440

---

### Post by ByteJuggler on 2008-01-17
Ok... I suppose this is the Ubuntu equivalent of locking yourself out of your car, with the keys inside...  (you need to use sudo to fix what you've done, but you can't because of what you've done.... catch-22)

To fix it I think your best bet is to boot with the LiveCD, then mount your hdd partition, then use the LiveCD's sudo to change the permissions on your installed "sudoers" file, to allow you to use your installed sudo again...

---

### Post by TwinkieFGR on 2008-01-17
I booted with the live cd
went to places and found the partition that ubuntu is installed on
after clicking the partition it was added to my desktop, labeled 'disk' (is this what you meant by mounting it? maybe my wires are crossed)
I opened the terminal and this took place

ubuntu@ubuntu:~$ sudo chmod 440 /etc/sudoers
ubuntu@ubuntu:~$

Assuming it worked I rebooted and loaded ubuntu from the hard drive.
...no luck.

I'm back in the live cd again, any suggestions?

---

### Post by PeterJS on 2008-01-17
When you boot to the live cd, there are two sudoers files, one in  /etc/sudoers for the live environment and another in /media/something/etc/sudoers which is the sudoers file for your  installed system.

---

### Post by TwinkieFGR on 2008-01-17
disk/media?
That's the only media folder I see, it contains *cdrom*, *cdrom0,* *sda1* and *sdb1*, all of which are empty

---

### Post by ByteJuggler on 2008-01-17
> **TwinkieFGR said:**
> I booted with the live cd
went to places and found the partition that ubuntu is installed on
after clicking the partition it was added to my desktop, labeled 'disk' (is this what you meant by mounting it? maybe my wires are crossed)
I opened the terminal and this took place

ubuntu@ubuntu:~$ sudo chmod 440 /etc/sudoers
ubuntu@ubuntu:~$

Assuming it worked I rebooted and loaded ubuntu from the hard drive.
...no luck.

I'm back in the live cd again, any suggestions?

Yes, after it appears on your desktop, double click the disk icon.  This mounts the partition under /media/disk and opens the folder so you can browse it using the nautilus explorer.

Now, you can either edit the permissions with the nautilus explorer, or open a terminal and do:

```
sudo chmod 440 /media/disk/etc/sudoers 
```

The command you tried (referring to /etc/sudoers) will change the mode of the livecd's filesystem's sudoers file (which obviously doens't help.)

---

### Post by TwinkieFGR on 2008-01-17
**SUCCESS!**

Thank you thank you thank you, I was getting scared I would have to reinstall and I still have no clue what I did to get my sound card to work. :D

---

