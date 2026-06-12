---
title: "Dual Boot on Thinkpad: Questions"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by PhilippHD on 2006-09-21
Hi everybody,
I recently got my new Thinkpad Z60m with pre-installed Win XP. Since my Desktop-PC is already running Ubuntu (no Dual Boot) and I´m really happy with it, I´d like to put that on my Laptop too. 
Still I want to remain one computer I can use in case I still need Windoze (probably for gaming). 

Dual Boot would probably be the best solution, but I still have some questions about it.

- Will Dual Boot make my Notebook slower ?
- Is there a way to use the ThinkVantage-Software of IBM on Ubuntu ?
- I know that there is a "Basic-OS" from IBM that is installed on every Thinkpad. Will it still be there when I re-install my Notebook ?

If there is a good HowTo on installing a Dual Boot System, plz post a link here.

Thx

---

### Post by ronmarley1 on 2006-09-21
> **PhilippHD said:**
> Hi everybody,
I recently got my new Thinkpad Z60m with pre-installed Win XP. Since my Desktop-PC is already running Ubuntu (no Dual Boot) and I´m really happy with it, I´d like to put that on my Laptop too. 
Still I want to remain one computer I can use in case I still need Windoze (probably for gaming). 

Dual Boot would probably be the best solution, but I still have some questions about it.

- Will Dual Boot make my Notebook slower ?
- Is there a way to use the ThinkVantage-Software of IBM on Ubuntu ?
- I know that there is a "Basic-OS" from IBM that is installed on every Thinkpad. Will it still be there when I re-install my Notebook ?

If there is a good HowTo on installing a Dual Boot System, plz post a link here.

Thx

I run dual boot on my ThinkPad R51 with no problems.  See below for some answers to your questions (sorry I could not answer all).
- Will Dual Boot make my Notebook slower ?
No.  It will boot faster in Ubuntu.
- Is there a way to use the ThinkVantage-Software of IBM on Ubuntu ?
I don't think so
- I know that there is a "Basic-OS" from IBM that is installed on every Thinkpad. Will it still be there when I re-install my Notebook ?
Yes, as long as you don't overwrite that part of the hard drive when creating the Ubuntu partitions.
If there is a good HowTo on installing a Dual Boot System, plz post a link here.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by davmac on 2006-09-21
1) There is a delay at boot up, while it waits for you to choose which OS to load. Once booted neither OS will be slower.

2) Don't know

3) From memory this is kept on a separate hidden partition. As long as when you're installing Ubuntu you make sure it steers clear of this everything should be OK.

If you're not comfortable with dual boot there is another option. You could install vmware server (see [http://www.vmware.com](http://www.vmware.com)) on WinXP and then install Ubuntu within that. Ubuntu (but not Windows) would be slightly slower but you get the advantage of being able to switch between them without rebooting.

The dual boot howto at [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html) is half decent (IMO).

Dave Mac

---

### Post by MartySkitch on 2006-09-21
Since you mentioned that you just want to put windows on your laptop just in case you might want to consider using VMWare and running window as a virtual machine.

---

