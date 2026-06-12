---
title: "Specific Apple-Intel releases or not? Which .iso should be used?"
date: 2015-12-10
forum: Apple Hardware Users
---

### Post by BobUgh on 2015-12-10
I've been reading this forum, and the instructions at [www.ubuntu.com](www.ubuntu.com) for a couple of weeks now, and I am confused. Some of the documentation seems to say the Mactel specific changes have been folded into the main release starting with Ubuntu 14 or earlier, and for most Macs, 14.04.03 (Trusty Tahr) is recommended. (There are inconsistencies about that too, but I am assuming pages recommending releases older than 14 are outdated)

Yet there are .iso and other images at ubuntu.com that are named in such a way that suggest otherwise.

At [http://releases.ubuntu.com/trusty](http://releases.ubuntu.com/trusty), the images look like
```
ubuntu-14.04.3-desktop-amd64.iso         05-Aug-2015 05:39  1.0G  Desktop image for 64-bit PC (AMD64) computers (standard download)
```
it is actually 1054867456 bytes. It is the one a newbie would download if they just went to ubuntu.com and clicked on download menus.

But there is also this page, which can be hard to get to, it can be navigated to from [http://releases.ubuntu.com](http://releases.ubuntu.com) by clicking on "Unsupported Ubuntu Images"
At [http://cdimage.ubuntu.com/releases/14.04/release/](http://cdimage.ubuntu.com/releases/14.04/release/) the files have names like

```
ubuntu-14.04.3-desktop-amd64+mac.iso         05-Aug-2015 05:47  1.0G  Desktop image for 64-bit Mac (AMD64) computers (standard download)
```
and it is actually 1052770304 bytes, smaller than the standard! The time stamp suggests it is newer, but that may not be when it was built.

Can anyone tell me why different releases, what is different, and which one should be used?

---

### Post by MikeBraxner on 2015-12-10
Stick with the *desktop-amd64.iso unless your hardware ***specifically requires*** the '+mac' version.

---

### Post by ian-weisser on 2015-12-10
> **BobUgh said:**
> It is the one a newbie would download if they just went to ubuntu.com and clicked on download menus.

Only if they were using your machine and your browser settings.
The http request from your browser includes the browser's hardware architecture. This is trivial to change or lie about - it's in your browser's settings.
Nevertheless, the server assumes the browser is telling the truth and refers to the appropriate image for your stated architecture.

So if you click on Download from a 32-bit system, you should be offered a 32-bit install.

Happily, when you create the install DVD, you can try it first to ensure the version of Ubuntu works on your hardware.

---

### Post by BobUgh on 2015-12-10
> **ian-weisser said:**
> ...
Nevertheless, the server assumes the browser is telling the truth and refers to the appropriate image for your stated architecture.
So if you click on Download from a 32-bit system, you should be offered a 32-bit install...

Thanks for that info. I don't remember when downloading any query or message that I was being automatically guided to the download appropriate for the machine I was on at the time. - I didn't know what I didn't know. Hmm, next time I think I'll change my user agent to iOS iPad and see what happens!

I think that is an incorrect assumption, that the machine one is using to perform the download will be the machine that the install will be done on. I bet there are many cases people are using a newer machine to make the download and bootable media, then will install on an older machine (that may not be bootable), and if that doesn't work, the old machine goes to the recycler. And if that happens to a newbie, they may never try Ubuntu again.

---

### Post by BobUgh on 2015-12-10
> **MikeBraxner said:**
> Stick with the *desktop-amd64.iso unless your hardware ***specifically requires*** the '+mac' version.

And how do I know if my hardware requires the +mac version?

I only ask after some googling and learning lots except what I want to know. It seems the +mac version has to do with some Macs having problems booting off the standard DVD, that info is 4 years old. If it is anything like that it means the installation software is different, but the installed bits would be the same. With that thought, I just realized the '+mac' version may not need files such as wubi.exe, but originally the "+" sign made me think it was everything-PC plus, not mac-only.

---

### Post by ian-weisser on 2015-12-10
> **BobUgh said:**
> I think that is an incorrect assumption, that the machine one is using to perform the download will be the machine that the install will be done on.
Well, of course that's not a valid assumption under ALL circumstances. But what is?
It is, however, usually a valid assumption for Ubuntu's target market - unskilled, first-time experimenters with Linux. And, as you discovered the alternatives, so will others.
A decade of experience has shown that simply asking users about their architecture is both thoroughly unreliable and rather scary and off-putting to potential new users.

Knowing what a user agent is indicates that you may not be unskilled, and not put off by such questions.


> **BobUgh said:**
> I bet there are many cases people are using a newer machine to make the download and bootable media, then will install on an older machine (that may not be bootable), and if that doesn't work, the old machine goes to the recycler.
Ressurecting an older machine properly requires time, skill, and experience. Done it, too.
 I think it seems an inappropriate project for a new, unskilled user's first experimentation with Linux and Ubuntu.
There are threads in this forum that agree - new users frustrated that they have bitten off much more than they can digest. Like painting - it's not easy to do right the first time.

Happily, I think you are up to the challenge.

> **BobUgh said:**
>  And if that happens to a newbie, they may never try Ubuntu again.
So what?
There are many, many 'I-hate-Ubuntu-and-I'm-never-coming-back' threads in this forum. And there are also many, many 'I'm-back-after-years-in-the-wilderness' threads.

---

### Post by MikeBraxner on 2015-12-10
> **BobUgh said:**
> And how do I know if my hardware requires the +mac version?

Two thoughts: 

First, if your hardware is fairly recent, say, within the last two/three years ... don't worry about it, just pull the version from Ubuntu's download page.

Two, just go ahead and try it ... do yourself a favour, and don't over-think everything. Worst case, you get stuck on boot. Ten/Fifteen years ago, downloading an ISO could be an absolute pain ... these days, it takes minutes. Once you have a working base, install something like TimeShift, and run backups on your system stuff every so often ... and then go ahead, and screw around with your system all you want. 

Frankly, there is no better way to get comfortable with your system, then to loose the inhibition instilled by MS/Apple, that implies that users can only screw things up. Sod it. Get your hands dirty, and try out whatever comes your way ... that's what backups are for.;)

---

### Post by BobUgh on 2015-12-10
The system I am considering installing it on is a 2010 MacBook Pro and it isn't usually connected to the internet. My machines that do have 24/7 internet access (albeit mediocre) already run Ubuntu or I'm not interested in installing Ubuntu on them. The circumstances I am in are rather unique, my point is it is a bit of leg work for me to just try one install download after another. Also, I am waiting for some mail-order blank DVDs to arrive, so it is either read the forums (where I saw the +mac files and made me ask the question on this thread) and/or figure out how to create a bootable usb install which I am also reading up on... Unrelated comment: in my ancient experience new hardware is less likely to work with Ubuntu because it takes a year or so for Canonical to catch up. Actually for Ubuntu to work on Apple hardware is no small task so it is a great achievement what Canonical has been able to do.
> Worst case, you get stuck on boot.
If I try one download and it won't boot off off the install media, no big deal. Worse is it boots and fails part way through the install and then I can't boot off the hard drive. Worst case is it actually installs and appears fine, but months/years from now I find out something is not working and I should have installed a different iso, for example if you want to say worst case, something like the fan control doesn't work and it gets too hot. **If the only differences between the two *.iso files is the installation code and the resulting installed code is the same (which is what I am starting to assume), OK, but I didn't know that, so that is why I asked the question.** At least 2 others recently have described the Mac install instructions as "convoluted" so I am not alone. I used a PC to fetch the .iso file, I probably got the right file but now I think if I had used the target Mac to find the the probability of getting the right one would have been higher.

I have been using various flavours of unix for about 35 years now, and first used Ubuntu ~2008. I still have 4 CDs (the install fit on CD then) from that era that don't boot on apple hardware, and I didn't expect apple to boot them. When Ubuntu switched their GUI, I started using it less and over time, 3 years ago I got a mac and over time used OSX more.  For example, I still don't know how to control what Ubuntu (Unity?) does after a SD card that looks like a camera is plugged in; I actually hate it when external storage devices are auto mounted (but I've learned to accept it) but I still get p off when *.jpg are auto imported. It was easy for me to find how to control settings like that in the old GUI. It has been years now that I've been on the new interface but just within the last month did I learn I can get to more applications by clicking on dash home then what looks like a greyed out hieroglyph near the BOTTOM of the dash home window, it never occurred to me to click on a dimmed icon near the bottom for more choices...

The Ubuntu system I do have is on a more than 10 year old Acer notebook. Because of the age of the Acer I am investigating dual booting the 2010 MacBook, move my Ubuntu data to that, and send the old Acer to the recycler. If installation and using becomes too troublesome, my next adventure would be to buy a more recent Mac and set up Ubuntu in a virtual machine within OSX.

---

