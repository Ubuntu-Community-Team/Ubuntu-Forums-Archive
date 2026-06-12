---
title: "Big problem, please help!"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by cl_audio on 2007-06-08
Hey! I have a big issue.

When ever i put ubuntu into sleep mode (by either shutting the lid on my laptop or clicking stand by/sleep)
the fan on my laptop constantly keeps running.

I have an Acer 5100 Laptop, using the latest version of feisty fawn.

Also, when i boot up (using grub) a msg pops up saying bios bug found then it just continues to load normally.

Also, the hibernate feature doesn't actually suspend my laptop, it just acts as sleep mode.

Thanks everyone in advanced and hope for some helpful responses!


Claudio

---

### Post by Pragmatist on 2007-06-08
> **cl_audio said:**
> ...when i boot up (using grub) a msg pops up saying bios bug found then it just continues to load normally.


Please post the exact message if possible.

---

### Post by cl_audio on 2007-06-09
lets not worry too much about the bios bug, my problem is that since the new ubuntu (fiesty fawn) everytime i place it in sleep mode (by shutting the lid, or going directy to sleep mode) my computer fan keeps running and it gets really hot... please someone help

---

### Post by Nikron on 2007-06-09
You realize that bios supplies the information for acpi to run properly, right?  Also, go to /proc/acpi/fan/ and list the contents of that directory.  If /proc/acpi/ does not exist, try 'sudo modprobe fan'

---

### Post by cl_audio on 2007-06-11
yea I understand what you are saying, but once again, when i was running edgy eft, there were no problems like this, and all the sudden with feisty fawn its doing this.

---

### Post by cl_audio on 2007-06-12
I did what you said, in /proc/acpi/fan there are no contents.Trying sudo modprobe fan doesn't echo back anything

---

### Post by Pragmatist on 2007-06-12
> **cl_audio said:**
> yea I understand what you are saying, but once again, when i was running edgy eft, there were no problems like this, and all the sudden with feisty fawn its doing this.

Try selecting an earlier kernel from the GRUB list (which you should see when you boot your computer).

---

### Post by Inxsible on 2007-06-12
Have you installed uswsusp ?

The acpi suspend and hibernate do not work on all architectures. Installing uswsusp helps quite a lot of ppl. Alas ! not everyone !

```
sudo aptitude install uswsusp
```

You will also need to change the hibernate.sh and sleep.sh files in the /etc/acpi folder. Let me search for the changes and get back to you.

---

### Post by bradmayne on 2007-06-22
your not the only one! I'm running feisty fawn on a toshiba satellite a135 s4527 with a dual core pentium. I am receiving a bios error on boot (i am running a dual boot with Vista home premium). I installed the uswsusp. When I try to put my laptop to sleep i have problems too! I did a post a few weeks ago about this and someone told me they didn't think i could be having problems because of feisty! Let me know if you solve your problem as i haven't been able to figure out how to yet!:o

---

