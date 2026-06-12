---
title: "How do I move everything except OS to new partition"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-26
When I setup Ubuntu I didn't make a seperate partition on the drive. I would like to repartition my drive and move everything except the OS to this partition in case I need to reinstall my OS. I have already done this once because of my playing with things I didn't reeally understand. Gottaz learn somehow:p 
Larry

---

### Post by petri on 2006-09-26
Just see my sig :D

---

### Post by Marsolin on 2006-09-26
The best way to do this is to copy everything in your /home directory to the new partition. You can them change /etc/fstab to use the new partition as /home. The next time you need to reinstall you can completely overwrite the / partition to clean it out and again tell Ubuntu to point to the second partition for /home. All settings will be restored instantaneously. You will need to do this before logging into KDE or Gnome though.

---

### Post by HareBall on 2006-09-27
> **petri said:**
> Just see my sig :D

Well, I tried this. Now I can't access anything:( 
When I boot to Ubuntu I get a message that says:
"Your home directory is listed as:
'/home/larry'
But it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session."
I chose yes and that just took me back to login and it still wouldn't login. I chose no the next time I booted up and it did the same thing.
I went back to the live cd and used the terminal to try to reset everything. This didn't change what happened when I booted up.
Now what do I do? I can reinstall the OS and lose everything. Most of which I have saved on cd's and dvd's. But there are some things I don't have saved that I would rather not lose.
This the main reason I wanted to do this in the first place:) 
Larry

---

### Post by HareBall on 2006-09-27
> **Marsolin said:**
> The best way to do this is to copy everything in your /home directory to the new partition. You can them change /etc/fstab to use the new partition as /home. The next time you need to reinstall you can completely overwrite the / partition to clean it out and again tell Ubuntu to point to the second partition for /home. All settings will be restored instantaneously. You will need to do this before logging into KDE or Gnome though.

If I get what I have already done straightened out, I will try this next time](*,)

---

### Post by HareBall on 2006-09-27
> **HareBall said:**
> Well, I tried this. Now I can't access anything:( 
When I boot to Ubuntu I get a message that says:
"Your home directory is listed as:
'/home/larry'
But it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session."
I chose yes and that just took me back to login and it still wouldn't login. I chose no the next time I booted up and it did the same thing.
I went back to the live cd and used the terminal to try to reset everything. This didn't change what happened when I booted up.
Now what do I do? I can reinstall the OS and lose everything. Most of which I have saved on cd's and dvd's. But there are some things I don't have saved that I would rather not lose.
This the main reason I wanted to do this in the first place:) 
Larry

I really hate to bump my message, but I'm not sure it will be seen on the second page. I really need help here.

---

### Post by petri on 2006-09-27
First of all you can save all your files from your harddisk with the LiveCD if you have somewhere to put them, extern hd, extra hd (borrow?) DVDs?

1. Did you try this:
> What if it doesn't work?
You know, it really should work, but if you somehow messed up your /etc/fstab and didn't configure it correctly... well, that's why we have a live CD, so we can fix things.

Boot up the live CD, go to a terminal, and type:
```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
```

Then, reboot. 

2. Did you everything as the guide says? That might be difficult to remember now.

3. In terminal do this and paste result here.
```
gedit /etc/fstab
```

4. I'm sure we will fix this ;)

---

### Post by uk_sphinx on 2006-09-27
if you copy everything to the new partition dont you have to tell ubunto which partiton the startup files are on or something?
like when you install it

i just installed ubuntu fresh and i gave my second partition /2 as a drive name and instead of giving me a seperate drive on system/drive  it put the sperate partiton in a file called /2 in the main partition

---

### Post by HareBall on 2006-09-27
> **petri said:**
> First of all you can save all your files from your harddisk with the LiveCD if you have somewhere to put them, extern hd, extra hd (borrow?) DVDs?

1. Did you try this:


2. Did you everything as the guide says? That might be difficult to remember now.

3. In terminal do this and paste result here.
```
gedit /etc/fstab
```

4. I'm sure we will fix this ;)

Here are the results;
union / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid nodev 0 0
/dev/sdb5 swap swap defaults 0 0

---

