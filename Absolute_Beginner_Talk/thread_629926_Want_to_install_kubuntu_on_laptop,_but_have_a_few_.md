---
title: "Want to install kubuntu on laptop, but have a few questions"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-12-02
Hi, I really like Kubuntu and want to spread to love to my laptop,but have a few questions

1.  If for some reason I want to go back to Vista, will I have an issue with getting it back via the boot disk

2.  I heard that kubuntu is hard on a laptops HDD because it causes it to spin at full speed forever, is this true? if so is there a way to fix it

3.  I know how to start cool n' quiet in ubuntu, now how do I do it in kubuntu

4.  How do I configure wireless in kubuntu

5.  is there anything else that I need to worry about

Thanks

---

### Post by siciliancasanova on 2007-12-02
Maybe find out about your graphics card also, do a search for it and any problems.

---

### Post by Dapman01 on 2007-12-02
> **siciliancasanova said:**
> Maybe find out about your graphics card also, do a search for it and any problems.

I don't the the Graphics will be a problem it has a 7600 in it

---

### Post by nae5 on 2007-12-02
> 1. If for some reason I want to go back to Vista, will I have an issue with getting it back via the boot disk


If you dual boot, vista will still be there and you will be able to pick which os you want to load when you boot up.

> I heard that kubuntu is hard on a laptops HDD because it causes it to spin at full speed forever, is this true? if so is there a way to fix it

really? never heard of this.  If it does then its unsupported hw or...

> 3. I know how to start cool n' quiet in ubuntu, now how do I do it in kubuntu

4. How do I configure wireless in kubuntu

Ubuntu and Kubuntu are basically the same thing, the main difference being that ubuntu uses gnome and related apps and kubuntu uses kde and related apps.  gnome and kde are desktop environments.  

So, configuring the wirelss will be the same if you were able to do it on the same laptop with ubuntu.  If you used ubuntu on another pc, you might want to make sure your wireless card is supported "out of the box", if not then you can try the restricted drivers manager ndiswrapper or fwcutter once the install is complete.

---

### Post by Dapman01 on 2007-12-02
Thanks, now where do I go to configure wireless and cool n' quiet

---

### Post by nae5 on 2007-12-02
For the wireless card, it depends on which kind it is. Have you already installed kubuntu on this laptop?
If so, and the wireless card is not working did you try finding a driver in the restricted drivers manager?

If that does not work you need to search the hardware section for your wireless card, and take steps that others have used to get it working, that is how i have made ubuntu/kubuntu work with multiple cards. - if this becomes hard i can help you search for answers.

Cool n'quiet will probably be done the same way in kubuntu as ubtuntu, try search the 64 b forum or google or amd site

lspci in terminal will tell you w/less nic type

---

### Post by PeterJS on 2007-12-02
> **nae5 said:**
> 
really? never heard of this.  If it does then its unsupported hw or...


This is an issue with the entire *buntu family, and it's really not their faults. Ubuntu respects the hardware defaults, unlike windows, so manufactures never had to use sane default settings. There's been some debate as to who's problem this is, and how to fix it, should Ubuntu use it's own settings, or should hardware manufactures step up and start using sane default settings for power saving modes.

---

### Post by nae5 on 2007-12-02
huh..  well ok, seems standards from the hw makers would be best, no? but both will probably end up happening. . ive never had hd problems with ubuntu so i guess im just lucky

---

