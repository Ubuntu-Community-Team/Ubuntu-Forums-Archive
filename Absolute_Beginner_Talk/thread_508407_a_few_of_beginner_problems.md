---
title: "a few of beginner problems"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by brycegg on 2007-07-24
Hello, i recently I've installed ubuntu, and I've come across a few problems, it would be awesome if i could fix them all. :)

anyway here is a list of them..

1st

When i first installed, my Internet was disabled, because i would need to add two custom DNS servers

4.2.2.2
4.3.3.3

When i add them, everything works fine, except sometimes(usually when i '**do**' something, my Internet stays on if i sleep and leave it on) it reverts/resets back to the 192.x.x.1, thus disabling my Internet.. though i can still stream radio, and talk on messenger..

2nd

I want to get my ATi Radeon x600 graphics card to work, but it isn't working, and a friend told me ATi has no support for linux, but after some searching i think there is.. 

3rd

I was installing some codecs and stuff, using EasyUbuntu which i installed yesterday, and now whenever i boot into the desktop it tells me "Fails to initialize HAL".. then when i go to the NTFS config tool, it gives:

Error : An error occurred when trying to initialize HAL. Can't search for new partition.

So now i can't view my XP files or my USB HD

note: this is a side question.. how can i view my XP/External HD?


Can anyone help me with these..? Help would be highly appreciated.


hope i worded it correctly..


- bryce

---

### Post by zanglang on 2007-07-24
Not sure about the others, but for 1, your DNS settings were probably getting overwritten by settings returned by your DHCP server. You can either somehow configure the server to just return 4.x.x.x, or if you're not sure how, you can add a few lines into '/etc/dhcp3/dhclient.conf':
> prepend domain-name-servers <DNS server IP here, e.g. 4.x.x.x>;
Repeat as necessary for each DNS server IP.

---

### Post by brycegg on 2007-07-24
> **zanglang said:**
> Not sure about the others, but for 1, your DNS settings were probably getting overwritten by settings returned by your DHCP server. You can either somehow configure the server to just return 4.x.x.x, or if you're not sure how, you can add a few lines into '/etc/dhcp3/dhclient.conf':

Repeat as necessary for each DNS server IP.


Thank you!! When i restarted my internet needed not to be reconfigured! :)

does anyone know anything about the others?[-o<

---

### Post by tombott on 2007-07-24
When you say your ATI graphics card doesn't work what do you mean?
Do you mean you can't get max screen res etc.?

If so try following [this guide]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") for instructions on installing ATI drivers.

---

### Post by brycegg on 2007-07-24
> **tombott said:**
> When you say your ATI graphics card doesn't work what do you mean?
Do you mean you can't get max screen res etc.?

If so try following [this guide]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") for instructions on installing ATI drivers.

Desktop Effects are totally unusable, my max res is 1024x768.. i cant use 3D chess :P and.. thats all i can tell.

---

### Post by brycegg on 2007-07-24
anyone? [/bump]

---

### Post by jzurawski99 on 2007-07-25
Below is something I posted in another hal issue thread that worked. It might apply to the 3rd problem on your list.


Re: the infamous Failed to initialize hal error 

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update via Ubuntus automatic update system (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes" 

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

************************************************** *************************************

Again, I have no idea what any of this effects. All I know is that after following the above I regained all hardware functionality. I hope this helps some of you.

JZ

---

### Post by tombott on 2007-07-25
> **brycegg said:**
> anyone? [/bump]

Did you try installing the ATI drivers?

[[COLOR="Red"]Guides[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29")

---

