---
title: "KVM switch"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Skittle on 2007-11-11
Hello all. 
I bought a USB KVM switch today, and it works wonderfully, for the most part. I can boot to both of my computers, and it works on both Windows XP and Ubuntu. The problem is, when I switch to the computer that dual boots XP and Ubuntu, for whatever reason, when the menu comes up to boot to windows or ubuntu, the keyboard won't work, and I'm forced to boot to the default system. (which is ubuntu, and I'm perfectly fine with that :D it's just a pain in the butt.)

Any solutions?

---

### Post by expatCM on 2007-11-11
If you use Startup-Manager (in the repositories) and change the resolution to the same as your desktop (first tab), does that help?

---

### Post by Skittle on 2007-11-11
> **expatCM said:**
> If you use Startup-Manager (in the repositories) and change the resolution to the same as your desktop (first tab), does that help?

Hate to ask, but I'm completely new to linux of any sort... How do I get to Startup-Manager?

---

### Post by expatCM on 2007-11-11
go to System / Administration and then select Synaptic

Click on Search and enter startupmanager

Look down the list returned and select startupmanager and install.

When it is installed you will find the program under System / Administration

---

### Post by expatCM on 2007-11-11
sorry but a short follow up ......  if you do not see the program in the search list would you please post back and say so .....   If you are new you may have left your sources.list alone and that may mean that the program is not found since it is in another repository .....

---

### Post by Skittle on 2007-11-11
> **expatCM said:**
> go to System / Administration and then select Synaptic

Click on Search and enter startupmanager

Look down the list returned and select startupmanager and install.

When it is installed you will find the program under System / Administration
When I click on search and search for startupmanager (I also tried startup-manager), nothing gets returned.

---

### Post by expatCM on 2007-11-11
probably that in your sources.list there are still repositories which are commented out.

Have a look at the following and see if any of the repositories have # at the start of the line

sudo pico /etc/apt/sources.list

If there are ... you can remove the # and then press Control O to save the list and then 

sudo apt-get update

When you then return to Synaptic you should be able to find the program ....

---

### Post by Skittle on 2007-11-11
> **expatCM said:**
> probably that in your sources.list there are still repositories which are commented out.

Have a look at the following and see if any of the repositories have # at the start of the line

sudo pico /etc/apt/sources.list

If there are ... you can remove the # and then press Control O to save the list and then 

sudo apt-get update

When you then return to Synaptic you should be able to find the program ....

Mkay there are a few with # at the front.
some have # and some have ##. Should I change all or just the ones with One #?

---

### Post by HermanAB on 2007-11-11
The problem with the keyboard at startup is a common one.  The USB driver is only loaded later, so you need a PS2 keyboard for the boot menu.

---

### Post by Wiebelhaus on 2007-11-11
Say man , Take the USB based KVM back and get a real one , We had one lasted 3 weeks before one of the techs killed it with fire , real piece of crap.

---

### Post by Skittle on 2007-11-11
> **sx66gns said:**
> Say man , Take the USB based KVM back and get a real one , We had one lasted 3 weeks before one of the techs killed it with fire , real piece of crap.

Yeah? Hm. Alright... Well no loss, I didn't buy it, I actually just jacked it from the IT storage room at work. I work in the IT department and they pretty much let me take anything I need unless they're using it. 
I had a PS2 based switch, and still do, but my mouse is USB and for some reason or other, it won't work at all with a USB to PS2 adapter. I've tried everything and came to the conclusion that Dell laser mice aren't compatible with them.

---

