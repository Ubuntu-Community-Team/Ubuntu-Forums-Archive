---
title: "iMac Intel Core 2 Duo requires to be booted twice"
date: 2019-06-13
forum: Apple Hardware Users
---

### Post by mulder-fox-n on 2019-06-13
Hello,

After a recent set of Ubuntu updates, approximately on or around May 23rd 2019, my iMac Intel Core 2 Duo now does not work on the first boot attempt. I have had Ubuntu running on this machine since January 2015 and never experienced this problem until now.

System details:

Ubuntu 18.04.2 LTS

Memory        3.9 GiB
Processor    Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2
Graphics    AMD® Rv610
GNOME        3.28.2
OS type        32-bit**
Disk        241.7 GB

_First boot attempt_: seems normal until I get a blank maroon screen for maybe five seconds then I get a black screen. Nothing happens and pressing keys does not get any response. The only option is to press the power button and switch the machine back off.

_Second boot attempt_: seems normal(ish) but goes to the Grub2 menu screen where I have to manually select *Ubuntu. This is not a problem in itself and selecting *Ubuntu allows Ubuntu to boot up properly and take me to the user login screen. All is normal after that.

I'm just wondering why the first switch-on and boot attempt gives me neither the Grub2 menu screen or even the normal user login screen? from January 2015 until May 2019, switching the machine on has taken me straight to the user login screen. There was a large update recently and immediately, the next time I switched on the machine, the problem as described above, commenced.

Any suggestions or advice gratefully received. After 35 years of owning computers and 23 years of internet access, if I have learned one thing, it is that I will not be the only person who has encountered this problem.

** In case anyone wonders, I have found that running the 64-bit version of Ubuntu uses up a lot of system resources and the machine struggles quite a lot. Running the 32-bit version, it actually runs faster than when it was a brand new iMac in January 2008, albeit with the 1GB of memory upgraded last year to 4GB.

Best regards,

Miceal :-)

---

### Post by mulder-fox-n on 2019-06-23
Hello folks,

After posting my initial post, I did not then sit back and hope someone else would solve the problem for me. I kept searching on the internet for an explanation and also kept playing around with the GRUB2 interface, specifically the [COLOR=#b22222]**Advanced options for Ubuntu**[/COLOR] option in the initial GRUB2 menu. I noticed that I had no less than six options, basically three versions of something and each of them also had a Safe Mode version as well. I could see that each was a succeeding version of some part of the OS but I did not understand what part. They ended ...452, ...451 and ...450. I kept trying ...452 and that just caused the black screen dead end as described in my original post. I was going to try ...451 at the next boot but was a little wary of that in case it caused a major problem of some kind.

Then I found this webpage: [https://www.howtogeek.com/196520/grub2-101-how-to-access-and-use-your-linux-distributions-boot-loader/](https://www.howtogeek.com/196520/grub2-101-how-to-access-and-use-your-linux-distributions-boot-loader/)

That page explains that, among other things, [COLOR=#b22222]**Advanced options for Ubuntu**[/COLOR] has access to at least one older version of the Linux kernel, in case a kernel update has a problem with the system, you can then try the older one. So what has been happening to my machine is:

1) I switch it on and it tries to boot using the ...452 kernel, which doesn't work and I end up with a black screen and a dead end.
2) I switch the machine off and then back on and GRUB2 must know it has already tried ...452 and that didn't work so it then regresses and tries ...451, which does work. Hence the double boot attempt that was required ever since the major upgrade, including a kernel upgrade I am guessing, a bout four weeks or so ago. With my machine being over 11 years old now, I did not want to cause a physical failure of the power button or some other part through the doubling of the switch on process.

So now, hopefully, thanks to the webpage linked above, I can force the first boot attempt into the GRUB2 menu by holding down a Shift key from power on, and then select [COLOR=#b22222]**Advanced options for Ubuntu**[/COLOR], and then select the ...451 kernel. This should hopefully allow Ubuntu to boot up successfully the first time, albeit with a manual expedition into GRUB2. I hope that, if someone else experiences this problem, this information will be of help to them. i wonder if this is just a problem affecting my iMac Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2? I also wonder what will happen at the next kernel upgrade, or worse, the one after that, when the ...452 kernel is the oldest available and I cannot revert to the ...451 one anymore!?! That's assuming that ...453 and onward don't work either.

Best regards,

Miceal :)

---

