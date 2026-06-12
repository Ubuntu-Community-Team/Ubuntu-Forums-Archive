---
title: "latest update not so good"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by jasonk on 2007-04-12
Hi everyone,
yesterday before i left from work i updated 4 of our ubuntu machines with the latest updates.  I think it was the new kernel headers.  When i got back to work this morning all four of the machines were sitting at the log in page.  This was weird since they were all just locked last night.  i've figured out that now every time the screensaver comes on it is logging out.  Even if you try and go to the screensaver config it's logging us out.  I tried uninstalling gnome-screensaver and installing xscreensaver and the same thing happened.  Are these four machines alone.  Can someone help me fix it?  thanks.  I'm using edgy, and it's been fully updated.
thanks,
jason

---

### Post by whitefort on 2007-04-12
I can't help, but I thought I'd post and let you know you're not alone.

I think you'll find it's not just the screensaver - I found I was getting that 'crash to login' every time I tried to run some programs too.

I THINK it means you need to re-install the video drivers, but be careful.  I followed the instructions on how to do this, and still ended up with a crippled machine (couldn't get past a non-graphic login prompt).   In the end, I had to restore the whole system from a backup.

I'm still really annoyed about this, and I don't think I'll be accepting any more updates in future.  This is the second time something like this has happened in just a few months.

But I'm sorry to sound like a Gloom-Merchant.  Hopefully you'll have more luck at reinstalling the drivers than I did!!

---

### Post by jasonk on 2007-04-12
thanks for the tip, i didn't know it was just a video driver issue.  I re-ran envy, and everythings working great now.  envy's a great program that automatically detects, downloads, and installs your video drivers.  here's some simple steps to get it workin so you don't have to start all over next time. from terminal type:

If you already have envy first type:
sudo aptitude purge envy

sudo rm -R /usr/share/envy

After that or if you've never had envy installed type:
wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

sudo dpkg -i  envy_0.8.1-0ubuntu6_all.deb

then press Alt+Ctrl+F1 to kill X-Windows and type

envy


then follow instructions.  it's a great program

---

### Post by whitefort on 2007-04-13
Thanks, Jason.  I'm just shocked and delighted that I actually managed to post something that someone found helpful!!!

Thanks for the recommendation about Envy.  It's nice to hear a first-hand account of something like that.

I'm still not sure if it would help with this particular machine, because it's a widescreen laptop which I bought with Ubuntu pre-installed - I suspect it the software might have been tweaked in some arcane way to make everything work, and that a normal attempt to update drivers would banjax things.

Now that I've got the laptop all set up exactly how I like it again, I might do another full disk image and try the updates again, then try envy.  If it doesn't work, I can still restore the disk and no harm will have been done.

In fact, I think for that machine I might do a full backup in future before applying ANY updates.  Ubuntu is way better than windows, but windows never made a habit of breaking my machine with their patches...

---

