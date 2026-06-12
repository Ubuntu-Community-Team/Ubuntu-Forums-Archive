---
title: "Problems with corrupt &quot;.deb&quot;'s"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by bradyboo222 on 2007-02-19
I am new to linux and I have a faily complex problem... I think:

I have three laptops:
The computer I am now on is the only one that has internet. But it can't burn cd (or read them for that matter). {HP pavilion}

I have another laptop with a cracked screen it does have the capability to burn CD's but it won't go on the internet. {Toshiba Satellite}

The third is an older computer whose OS crashed. This is the one i am trying to get linux on. {IBM thinkpad} 

Plus i have an external hard drive to move stuff around.

Downloaded Ubuntu (edgy eft) on this one and got it over to the second one and burn a cd. I put the cd in the thinkpad and booted from the cd. It went through the whole routine fine until i got to "Installing base system" or whatever and around 6% is gives me an error message that say such-and-such.deb is corrupted. I clicked continue and it give me like 15 more of the same messages and all are .deb files. Found out that the md5sum thing is fine for the .iso file that I used to burn the cd and i burnt like 3 cd's two of them at super low speeds. 

I don't know what to do next and If anyone could give me any words from the wise about partitioning that would be great.

---

### Post by lhtown on 2007-02-19
OK, you say the thinkpad is an older computer. Did you try the live CD or does it not have enough memory? 

From your description, I am wondering if the hard drive on your old Thinkpad is the problem. I am not sure exactly how the installer works, but I think it copies everything to the hard disk and then "installs" it. It sounds to me like maybe it is finding errors in the files that it copied. Of course, it might also be a problem with your CD drive being flaky.

If the problem is the hard drive, the live CD should work fine if you have enough memory.

---

### Post by lhtown on 2007-02-19
As far as partitioning, the default is usually fine for most people. A lot of us like to install our home directory in a separate partition so that we can reinstall from scratch without having to reload our personal data.

If you are one who likes to play with new distributions or beta distributions, you might want to leave an empty partition of about 5 GB just to install distributions  that you aren't really planning to use or want to test out.

---

### Post by bradyboo222 on 2007-02-19
If it was a problem with my hard drive or a problem with my optical drive would the same file keep giving me the same error message? Cause it is. 

And on the cd's i burned all the error messages occur in kinda the same area. the first one occurs pool/main/l/linux-source-2.6.17/...  (i might have mistyped somthing) and the rest occur in a similar pattern. I don't know if that helps. 

How would i go about seting up my partions with a space for a home directory?

---

### Post by bradyboo222 on 2007-02-19
apparently Memorex sux and that is what i was using and the only other media i have is Office Depot DVD+R..... I think i heard that i can use those but ..... i dunno how.... HELP...
and before  i forget: How good is Office Depot DVD+R for a media?

---

### Post by lhtown on 2007-02-20
Write once discs tend to be much more reliable than rewritable disks. I don't know about the brands you mention. I don't know why the same file would always give you problems unless it is a particularly large file and it is getting eaten up due to a lack of memory.

Unless you have like 192 MB of memory, you should be using the alternate install disk (not really a bad idea anyway since it tends to be more reliable).

---

