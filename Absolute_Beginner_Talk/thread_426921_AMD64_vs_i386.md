---
title: "AMD64 vs i386"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by FLCLFan on 2007-04-28
Right now I am running Feisty ADM64 on a Athlon 64 3000+ ([off topic] with Beryl, which is the best!) and I was wondering, is the AMD64 faster/better then the i386 version on a AMD64 processor? Or are they both the same?

Ps: Is there a way to get a 64-bit version of flash/shockwave for FF on feisty?

---

### Post by Churnd on 2007-04-28
I think 64bit shines the best when you have over 4GB RAM.  You might see some slightly faster processing/encoding times, but I haven't seen a benchmark to prove it yet.  I'm thinking about testing it out myself.

As for the flash:  [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

There's no native 64 bit flash for linux... you have to run 32 bit.

---

### Post by Nihil Videmus on 2007-04-28
64-bit means that w/each clock cycle the processor is handling 64 bits of data versus the traditional 32 bits.

As to which one is better a program that's made for 64 bits will be much better then a 32 bit one, the only problem being that not many programs are made for 64 bit processing, meaning that it'll revert to/emulate the 32 bit processing.

As to the 4GB of ram thing the problem is that a 32-bit operating system only has 4GB of virtual address space, which means that it won't recognize anything beyond 4GB memory. In reality most systems won't recognize more then 3.5GB of ram because the virtual address space is taken up by any device that uses memory mapping (which nowadays means anything that doesn't give analogue input like a PS/2 keyboard or ancient mouse).

Hope that helps; [this link]("http://4help.alienware.com/cgi-bin/alienware.cfg/php/enduser/std_adp.php?p_faqid=1289&p_created=1087006479&p_sid=_whzjSRh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTA1NCZwX3Byb2RzPSZwX2NhdHM9MzU2LDM1OCZwX3B2PSZwX2N2PTIuMzU4JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfZm5sJnBfc2NmX2NfbGFuZ3VhZ2U9MjA1JnBfcGFnZT01&p_li=&p_topview=1") has a pretty good explanation.

---

### Post by FLCLFan on 2007-04-29
Oh, I understand :) 

Thanks guys.

But as for the flash. To get it, do i have to downgrade FF to 32bit verson? Or is there another way?

---

### Post by Sef on 2007-04-29
Try [Gnash]("http://www.gnu.org/software/gnash/").  It can handle 64 bit, if i remember correctly.  It is available under Applications > Add/Remove.

---

### Post by Churnd on 2007-04-29
> **FLCLFan said:**
> Oh, I understand :) 

Thanks guys.

But as for the flash. To get it, do i have to downgrade FF to 32bit verson? Or is there another way?

If you use Kilz's script, it installs a 32 bit FF along with the "64 bit" version.  The executable will be "firefox32".  It doesn't touch the other version.

---

### Post by Spike-X on 2007-04-29
> **FLCLFan said:**
> Is there a way to get a 64-bit version of flash/shockwave for FF on feisty?

Go to [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/)
Add the repositories and get the key. Then, in the terminal, run the following commands:

```
sudo apt-get update
sudo apt-get install nspluginwrapper gsfonts-x11
```

Download flash player 9 from Adobe site [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz) 

Instruct the file to open with Archive Manager.
Extract the 2 files &#8220;libflashplayer.so&#8221; and &#8220;flashplayer.xpt&#8221; into the /usr/lib/mozilla/plugins folder. Then run the following command:

```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

If you return to the prompt with no error messages, that means it worked.

In the folder /usr/lib/mozilla/plugins/ you'll find the file &#8220;npwrapper.libflashplayer.so&#8221;.

Copy it into the folders: /home/.mozilla/plugins/ and /usr/lib/mozilla-firefox/plugins/ .

Now, try going on [http://www.youtube.com/](http://www.youtube.com/) and watch a video.

---

### Post by mistergq on 2007-04-29
Thanks, Flash now works in Firefox.  But Java still does not work.  I have installed the Java with automatrix, but that did not help, any other suggestions?

---

### Post by shankariyer on 2007-04-29
I did all this and copied 'flashplayer.xpt' & 'libflashplayer.so' to '/usr/lib/firefox/plugins', but no luck.

This is Feisty on AMD64 and FF version 2.0.0.3

---

### Post by Spike-X on 2007-04-30
> **shankariyer said:**
> I did all this and copied 'flashplayer.xpt' & 'libflashplayer.so' to '/usr/lib/firefox/plugins', but no luck.


Did you do that **before** running the nspluginwrapper command?

---

### Post by shankariyer on 2007-05-01
nspluginwrapper worked ! Initially I had not installed it, but later when I installed it the directory structure was a bit confusing.

All I've is /usr/lib/firefox and /usr/lib/mozilla-firefox pointing to /usr/lib/firefox. Following the instruction created a new directory /usr/lib/mozilla/plugins with 'nspluginwrapper' ( from the installation ). I moved it back to /usr/lib/firefox/plugins and it works now.

Thanks guys!

---

### Post by jcronkhite on 2007-07-16
This solution worked great for me as well!  I was considering downgrading to 32bit Feisty, but now I will not need to.  Thanks!

---

