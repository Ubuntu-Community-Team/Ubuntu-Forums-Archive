---
title: "[SOLVED] Linux won't boot after motherboard change"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-12-09
ok, here's the deal - I had the motherboard changed, and now when it "boots up", it stops at the step of "running Start-up scripts" with no disk activity or anything as far as I know....  I've changed the board before (not myself :p) and the only problem I had was with X and one command fixed it... I'm sure this is a simple problem to solve, but I'd like some help seeing as I have know idea what to do :p

In the mean time, I'm not finding myself inconvenienced in the least luckily ;)

---

### Post by sports fan Matt on 2007-12-09
geez ryan...

this process seems to be a pain in the butt for ya....Im glad I havent had that occur, although I do know how to (I was a techie in high school..greatest time in my life)

---

### Post by jordanmthomas on 2007-12-10
Try editing your grub line (press e on it while you can still select it in GRUB)
On the line that starts with 'kernel' make sure the word "quiet" is not listed.
Then, hit esc and then b to boot.

This will get rid of the splash screen while booting so you can see where it's hanging.

---

### Post by ryanVickers on 2007-12-10
I know where it's hanging - where it says "Running Start-up Scripts (and then some short path name...)" :p

---

### Post by jordanmthomas on 2007-12-10
Right, but which startup script?

---

### Post by ryanVickers on 2007-12-10
Will it list that in the mode you said?  cool :p  It just looked like there was one... but I'll do that and see I guess lol

---

### Post by mozetti on 2007-12-10
FYI - changing out the motherboard isn't just a simple swap in terms of the OS. There's a good chance that you'll have to re-install Ubuntu unless you just replaced the old mobo with the same model.

---

### Post by ByteJuggler on 2007-12-10
> **mozetti said:**
> FYI - changing out the motherboard isn't just a simple swap in terms of the OS. There's a good chance that you'll have to re-install Ubuntu unless you just replaced the old mobo with the same model.

True in general, but you're far more likely to get away with this using Linux that Windows... (ask me I've just upgraded CPU/Mobo/RAM/Gfx, my Linux booted but X failed [expected] and *that* was fixed with a few commands.  Been running happily on the new hardware since.  Windows otoh, well, lets just say it's not pretty.  And, to top it off,  there's some kind of problem between Vista and the Intel ICH9R controller chipset on my new board and the specific hdd's I've got which is making a fresh install extremely aggravating as well.  The problem causes the Vista installation to hang and never complete.  Oh the joy... )

---

### Post by Bartender on 2007-12-10
I second mozetti -
Have seen an existing Linux installation work on a different motherboard, but it'll only work if the motherboard is similar to the previous.  I'm guessing North and Southbridge chipsets have to be the same at least.
You'll probably have to re-install.  Make a separate /home partition this time so that a re-install doesn't wipe out all your personal data!
If you do have important personal data and a spare HDD laying around you could probably install to the spare drive and slave the old one...

---

### Post by ByteJuggler on 2007-12-10
> **Bartender said:**
> ... but it'll only work if the motherboard is similar to the previous.  I'm guessing North and Southbridge chipsets have to be the same at least...

Well, not here in my particular instance.  :-)  I moved from a Via based AMD 754 pin motherboard system with Promise+VIA Sata RAID/IDE and Via onboard sound with AGP ATI 9800XT,  to Intel Core2 CPU + Intel ICH9R SATA RAID + JMicron IDE controller + Realtek HD onboard sound and ATI PCI-E 3850Pro.  Totally different chipsets/architectures.  Pretty much couldn't move further if you tried.  The only things that stayed was the Hard drives and optical drives.    

To be honest, I wasn't expecting it work (nearly as well as it did), and originally decided to try it just for a laugh.  However, with a bit of hindsight/analysis, perhaps the success shouldn't be all that suprising -- If Ubuntu boots to a working desktop from a CD as it does, then clearly in principle it can do that from any medium (there'd nothing special about booting from CD that gives it that ability.   Linux clearly doesn't hardwire as much at install time as Windows does, and so takes to moving a little better, it seems.

All that said, in general I would still agree with you.  There's no guarantee that you'd be able to move your installation to a new motherboard and boot it up.  But it sure is worth a try IME.

To the original poster:  It's worth it to boot off the live CD, and having a look at the last entries in e.g. /var/log/syslog  (use e.g. the command "tail /var/log/syslog" to see the last entries in the syslog.)  You could also conceivably resize your current partition to allow you to make a /home partition, then move your files/folders there and then reinstall on the now root-only partition.  But whatever you do, back up your data before you start!

---

### Post by ryanVickers on 2007-12-11
well, when I did this the first time (Gigabyte/nvidia --> ASUS) in Linux, one command and I was back, but with windows just replacing all the drivers and re-activating (all super simple, just slightly annoying :p) was all it took.  Now, going the other way (back to Gigabyte/nvidia) windows is fine no problems at all (maybe they did something to it... :p) but Linux needs a little work and hence this thread...

---

### Post by dcstar on 2007-12-12
> **ByteJuggler said:**
> 
.........
If Ubuntu boots to a working desktop from a CD as it does, then clearly in principle it can do that from any medium (there'd nothing special about booting from CD that gives it that ability.   Linux clearly doesn't hardwire as much at install time as Windows does, and so takes to moving a little better, it seems.
..........!

The Live CD is designed to do a thorough hardware and environment probe because it doesn't know what it will be booted up on - all of this checking takes time.

Once a system is installed, it is no longer necessary to check for a lot of things so that code is not run, which means your system will boot up a lot quicker than if it was still run every single time.

It it a trade-off between what is useful to 99.99% of people who do not make major changes to their environment versus the tiny fraction who do make a change - and quicker booting for the majority is far more useful than doing a thorough hardware check every boot.

---

### Post by ryanVickers on 2008-01-01
Well, it all seems to work now... I didn't have to do anything really... just booted recovery mode to do some backups and applied some updates, then I thought what the heck I'll give it another try and it works :D

---

### Post by Martje_001 on 2008-01-02
> **ryanVickers said:**
> I know where it's hanging - where it says "Running Start-up Scripts (and then some short path name...)" :p
That's just before X starts. Press CTRL+ALT+F1 and login. Typ: **sudo dpkg-reconfigure xserver-xorg**.

Edit: sorry.. ignore this then.

---

### Post by ryanVickers on 2008-01-02
yeah, that's what I had to do - in recovery mode, I did that, it just made me pick a resolution, then I logged on as rot, installed updates, and then tried again and it worked! :D

---

