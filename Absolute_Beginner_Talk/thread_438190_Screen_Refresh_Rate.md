---
title: "Screen Refresh Rate"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Mikey C on 2007-05-09
Still having trouble resolving the interference on the screen. As a total newbe with Linux & Ubuntu, and having read Read Me's & books, and looked at forums.

The interference is at its worst when downloading updates, there are a mass of horizontal lines scrolling up & down the screen, the same happens when I close down Ubuntu.

Any good ideas?

Mikey C

---

### Post by laidback on 2007-05-09
Had a video problem with my latest mobo and Ubuntu, it kept flashing very quickly when I opened a new file or apps, very annoying. It didn't necesarily happen with other distros so I felt it was something rather odd with the video system/driver. After a week of frustration I installed a PCI-e card and disabled the onboard version, I went from nVidia Geforce 6100 on-board to nVidia Geforce 6200 16x PCI-e card. Sooooomuch better, in fact it cured the problem completely. Could you try something similar?

---

### Post by Mikey C on 2007-05-10
Thank you Laidback of Essex,
    
I will give this a try.

Mikey C of Chepstow.

---

### Post by laidback on 2007-05-11
Mike C,
If you're able to post the outcome I'd be interested.

Laidback

---

### Post by karachuonyo on 2007-05-12
Hi and sorry to burge in your post, but i also have a geforce 6200 agp which i managed to install after abit of bother. However on some games i only manage like 50 fps tops while when i was using a geforce TI 4400 a managed easily 200 fps from the same games. Is there something i should do different. thanks.:confused:

---

### Post by laidback on 2007-05-13
> **karachuonyo said:**
> Hi and sorry to burge in your post, but i also have a geforce 6200 agp which i managed to install after abit of bother. However on some games i only manage like 50 fps tops while when i was using a geforce TI 4400 a managed easily 200 fps from the same games. Is there something i should do different. thanks.:confused:
karachuonyo,
I'm no expert in this field, I'm searching in the dark much like many others. My nVidia 6200TC turbo is a PCI-e 16X, does that make a difference?. I don't play games so have little to compare performance with. All I can say is that I installed Feisty from the LIve CD and then almost immediately chose System>Administration>Restricted Drivers menu and selected nVidia. That was it. Now is my card running as it should? I don't know. It runs Googleearth which it didn't before but more importantly the screen is stable with no flashing. I typed (at the $ prompt) glxinfo | grep direct, the result was direct rendering :yes. Another thread said this showed things were OK. 
The info on my card say it has 256mb but can use 512. How I would get it to use 512 is beyond me. It might be much better if I could manage that. All the installation info is for windoz of course so that's no help.

---

### Post by karachuonyo on 2007-05-13
Well thanks for the reply. At least its working and google earth runs great. I just thought a nvidia card on the legacy list would have a less fps than on the newer so called vista recommended, or i just haven't grasped the whole concept of fps.

---

### Post by laidback on 2007-05-13
I agree, you might expect a legacy card to run slower. As yet I haven't come across any way in Linux of testing performance, even glxgears doesn't run as expected in Ubuntu. In 7.04 I cannot get it to report fps at all.

---

### Post by Mikey C on 2007-05-27
Thank you laidback of Essex, problem cured, now no interference due to refresh rate.

New graphics installed, BIOS was set to PCI and not AGP.

---

