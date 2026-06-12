---
title: "Wirelessly connecting to internet (MacBook)"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by lavadbx on 2007-09-03
First off, I apologize for even making this thread. I'm sure it's something really obvious that gets asked all the time. I'm not even sure if this is the correct forum. I just can't figure it out and the tutorials and things like that that are posted around the website about wireless connectivity just aren't helping me.

I own the newest MacBook (purchased in June) and up until yesterday had simply been running OS X on it. However, after a while I got bored and felt a need to mess around with my computer so I set it up to dual-boot Ubuntu. I didn't have any problem with the installation or getting both OS's to run side by side. My problem is connecting to the internet on Ubuntu. When I go to the Network or whatever it's called thing it only lists "Wired" or "Modem" as my options for connecting to the internet. What do I do to get a wireless option to show up?

I imagine it has something to do with drivers, but I can't find a place to download what I would need.

My ISP is bellsouth and my router is an "Westell Versalink" model. (I have no problems connecting on OS X, obviously.)

All help is appreciated.

---

### Post by lavadbx on 2007-09-03
I hope I'm allowed to bump. But this was almost on the third page.

---

### Post by overdrank on 2007-09-03
> **lavadbx said:**
> I hope I'm allowed to bump. But this was almost on the third page.

Hi can you tell us you wireless card model? You can use the lspci command in the terminal and post the output here. Also I assume you can connect wired to the internet.

---

### Post by Fornax-101 on 2007-09-03
well, there is a thread on how to set it up: [http://ubuntuforums.org/showthread.php?t=485579]("http://ubuntuforums.org/showthread.php?t=485579")

---

### Post by lavadbx on 2007-09-03
> **overdrank said:**
> Hi can you tell us you wireless card model? You can use the lspci command in the terminal and post the output here. Also I assume you can connect wired to the internet.

Is there any way I could get that from OS X? I don't have internet in Ubuntu so I can't copy and paste my results in Ubuntu and it's way to much to write down.

---

### Post by overdrank on 2007-09-03
> **lavadbx said:**
> Is there any way I could get that from OS X? I don't have internet in Ubuntu so I can't copy and paste my results in Ubuntu and it's way to much to write down.

HI you may want to look at what Fornax-101 pointed to on the mac books. I have no idea about mac books I was just trying to help but the link looks good. :(

---

### Post by lavadbx on 2007-09-04
> **Fornax-101 said:**
> well, there is a thread on how to set it up: [http://ubuntuforums.org/showthread.php?t=485579]("http://ubuntuforums.org/showthread.php?t=485579")

I'm having trouble understanding that tutorial. I get to the second part where it says > This will create a directory on your desktop called madwifi which has all the sources for the driver
Change into that directory (the source directory
[quote]cd $(HOME)/Desktop/madwifi[/QUOTE]

What does that mean?

---

### Post by Fornax-101 on 2007-09-04
You don't have to follow that section, instead download [this]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2372-20070525.tar.gz") and extract it.

Next you have to open the terminal and browse to where you have extracted it:
```
cd ~/Desktop/madwifi-ng-r2372-20070525/
```
after that you can continue to follow the tutorial from:
> Now compile the driver:
```
make
```
...

---

