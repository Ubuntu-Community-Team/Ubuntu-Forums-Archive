---
title: "Should I be worried?"
date: 2012-06-15
forum: Apple Hardware Users
---

### Post by Kopkins on 2012-06-15
I've been running Ubuntu on my MBP now for around 6 months. I don't remember it running this hot all the time. 

Right now, I'm listening to spotify and posting this. I have a few more programs idle in the background. My cpu temp is around 56 C, which isn't that hot. 

Whenever I watch a video or do anything a little bit cpu intensive, the temp usually jumps to at least 70-80 C. 

While running a virtual machine, or even listening to high quality music, the temps can jump as high as 90+ C. I saw one reading yesterday as 100 C.

The title asks my question.

I'm running Ubuntu 12.04 LTS on a MBP 8,1. 

Thanks.

---

### Post by sanderj on 2012-06-15
Yes, I would say 100 oC is very hot. My CPU temp is 52 oC, and can go up to 65 or 70.

So, yes, you should be worried. Unless, of course, the temp sensor progam is not working.

Tip: run OSX and see what the temperature is then.

---

### Post by Kopkins on 2012-06-16
In OS X, idle temp is at around 56 again. 

Playing two 720p youtube videos at the same time runs the temp into the 90's.

EDIT: I don't think it's a problem with the program or sensors. The computer is uncomfortably hot.

---

### Post by penguin359 on 2012-06-16
You haven't by any chance disabled acpi with a boot parameter like acpi=off have you?  I've heard someone did that and fried their laptop.

---

### Post by Kopkins on 2012-06-16
I would have to do that intentionally right? I haven't done that.

---

### Post by Kopkins on 2012-06-16
So what should I do? What can I do?

Kopkins

---

### Post by sffvba[e0rt on 2012-06-16
> **Kopkins said:**
> In OS X, idle temp is at around 56 again. 

Playing two 720p youtube videos at the same time runs the temp into the 90's.

EDIT: I don't think it's a problem with the program or sensors. The computer is uncomfortably hot.

Seeing as the temperature is also running too hot in OSX I think we can safely assume the problem isn't Ubuntu related.

I would suggest cleaning the vents/fan of the system.


404

edit: Also, please don't bump threads more than once every 24 hours...

---

### Post by Kopkins on 2012-06-16
My apologies for the bump. 

The fan is clean. There's hardly any dust that I can see. The vents as well.  Is there a more in depth cleaning that I could do?

---

### Post by sffvba[e0rt on 2012-06-16
> **Kopkins said:**
> My apologies for the bump. 

The fan is clean. There's hardly any dust that I can see. The vents as well.  Is there a more in depth cleaning that I could do?

There seems to be many guides on the Internet, [like this one]("http://complicatedtosimple.com/clean-dust-macbook/")...

I can however not vouch for the effectiveness/correctness of this and would suggest possibly taking it to an Apple Store to get cleaned out if still under warranty etc. 


404

---

### Post by Kopkins on 2012-06-16
> **not found said:**
> There seems to be many guides on the Internet, [like this one]("http://complicatedtosimple.com/clean-dust-macbook/")...

I can however not vouch for the effectiveness/correctness of this and would suggest possibly taking it to an Apple Store to get cleaned out if still under warranty etc. 


404

Thanks, it is still under warranty. I'll stop by an apple store soon.

---

### Post by Thymen on 2012-06-17
Can it be that your backlighting is set too high? I installed Ubuntu 12.04/64bit on my iMac, but had to get rid of it because the screen ran at it's full brightness all the time. Found no way to reduce it. And, while in OSX the system is reasonably cool even under heavy load, in Ubuntu it runs very, very hot.

If this is the case with you, better look around for a way to reduce backlighting before you fry tour laptop.

Thymen

---

### Post by kohoutek1 on 2012-06-25
Kopkins,

This is a widely known issue among Macbook users. There's even a couple of threads on it on these forums.

To cut to the chase, you should do the following:

1. ```
sudo apt-get repository ppa:mactel-support/ppa
```

2.  ```
sudo apt-get update && install macfancltd
```

3. ```
gksudo nano /etc/modules
```

4. Add to the end of modules:
   coretemp
   macfanctld

5. Save then reboot.

YOu should then notice a major improvement in fan operation and temperature control.

Hope it helps.

---

