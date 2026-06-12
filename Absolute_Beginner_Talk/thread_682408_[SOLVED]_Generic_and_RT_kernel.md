---
title: "[SOLVED] Generic and RT kernel?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-01-30
This is a total noob question, but, here it goes...

Recently, I've been having issues with VIA video drivers. I install the drivers from VIA, and they were a total joke, so I went back to openchrome. Here's where I'm confused...

In order to install the VIA drivers, I was told I had to be in the 2.6.22-14-GENERIC kernel, and not the RT kernel. So, I switched to it, installed the drivers, and they were garbage.

I switched back into the generic kernel, uninstalled the VIA drivers, installed openchrome, and thought everything was back to normal...

Now, in the generic kernel, I have no 3D rendering at all. It gives me a message telling me that it's not enabled (though, I've done all I could to the xorg.conf to enable it, and it SHOWS it's enabled), when I use glxinfo | grep render.

I couldn't understand it at all. Apparently, in the generic kernel, I'm unable to change the VIA drivers over to openchrome, but in the RT kernel, everything went back to normal.

So, my question is, what's the difference between the generic and the realtime? And, if I make changes to, say, the RT kernel, are the same changes applied to the generic?

Sorry for the lengthy post. Thanks for any help :)

---

### Post by cleverselfreferentialname on 2008-01-30
> **Nerdriot said:**
> This is a total noob question, but, here it goes...

Recently, I've been having issues with VIA video drivers. I install the drivers from VIA, and they were a total joke, so I went back to openchrome. Here's where I'm confused...

In order to install the VIA drivers, I was told I had to be in the 2.6.22-14-GENERIC kernel, and not the RT kernel. So, I switched to it, installed the drivers, and they were garbage.

I switched back into the generic kernel, uninstalled the VIA drivers, installed openchrome, and thought everything was back to normal...

Now, in the generic kernel, I have no 3D rendering at all. It gives me a message telling me that it's not enabled (though, I've done all I could to the xorg.conf to enable it, and it SHOWS it's enabled), when I use glxinfo | grep render.

I couldn't understand it at all. Apparently, in the generic kernel, I'm unable to change the VIA drivers over to openchrome, but in the RT kernel, everything went back to normal.

So, my question is, what's the difference between the generic and the realtime? And, if I make changes to, say, the RT kernel, are the same changes applied to the generic?

Sorry for the lengthy post. Thanks for any help :)

Well, when you install the driver, you don't actually change the kernel. You can modprobe or insmod a kernel module and add it to the running kernel, but the kernel on the disk doesn't change.

I don't know much about RT, but the goal of the patch it to reduce the amount of code in the kernel that wasn't pre-emptable as much as possible. This improves responsiveness.

---

### Post by dcstar on 2008-01-30
> **Nerdriot said:**
> This is a total noob question, but, here it goes...

Recently, I've been having issues with VIA video drivers. I install the drivers from VIA, and they were a total joke, so I went back to openchrome. Here's where I'm confused...

In order to install the VIA drivers, I was told I had to be in the 2.6.22-14-GENERIC kernel, and not the RT kernel. So, I switched to it, installed the drivers, and they were garbage.
.........
Sorry for the lengthy post. Thanks for any help :)

I tried (for quite a while) to get decent Via Unichrome 3D performance in Ubuntu from a previous PC using its inbuilt video, after I gave up and went out and purchased an old Nvidia chipset video card I had all the performance I needed and none of the Via Unichrome issues - and I wondered why I had wasted so much time with a chipset that has so many issues in Linux when just a few dollars solved all my problems.

Every PC I consider these days has to have a well supported video/chipset by Linux, and that means something like Nvidia because it makes the whole Linux experience so much smoother.

---

### Post by Nerdriot on 2008-01-31
Thanks, guys! :)

Dcstar, you're right; I think going out and purchasing an Nvidia would probably be my best bet. Especially since I have no desire to ever use Windows again, the most logical thing for me to do would be to purchase hardware that is compatible with Linux.

As for my VIA issue, I've given up. I re-installed Ubuntu after having made so many changes and such trying to get it to work, only to realize that the standard drivers installed with the Ubuntu cd works as well as they can possibly work, considering VIA refuses to release working drivers.

Some 3D games work, and some don't. Looks like I'm going to Nvidia. :)

Thanks again, guys!

---

