---
title: "Feisty Ultra ATA Problem"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by crondog on 2007-05-29
Hi,

I know there will be an easy solution to this because i am making this post :P

But here is my problem:
I had edgy dual booted with windows xp. Windows is on my 320GB SATA drive. Edgy was on my 40GB Ultra ATA drive and there were no problems. But my BIOS doesnt recognise the Ultra ATA drive for some reason but everything still works. I can access the Ultra ATA drive in windows and edgy.

I decided to do a clean install with the Feisty DVD. But the Live CD isnt recognising my Ultra ATA drive. So i thought i would upgrade the Edgy installation. So i did. There were no problems with that. I restarted. Chose the Feisty kernel and the system just hangs. Ok. So i thought i will try the Edgy kernel...Still hangs.

On the Feisty Live CD GParted doesnt recognise the Ultra ATA drive. Fdisk, Cfdisk and Sfdisk dont recognise the Ultra ATA drive either.

Is there a way around this? Am i doing anything wrong? Ive searched the forums and google but i am probably overlooking something (Everytime i get a chance to work on the i am really tired lol)

All i would like is a quick fix.

---

### Post by crondog on 2007-05-29
So no one can help....?

---

### Post by crondog on 2007-06-01
Well this sucks then doesnt it :(

---

### Post by Patrick K on 2007-06-01
Sounds like your problem is in the bios. I'm surprised you could access the drive at all without the bios seeing it. I suggest resetting the bios. You'll have to check your manual for how to do this. Some have an option in the setup screen, others require changing a jumper on the MoBo. Anyway, that where I'd look.

---

### Post by crondog on 2007-06-01
> **Patrick K said:**
> Sounds like your problem is in the bios. I'm surprised you could access the drive at all without the bios seeing it. I suggest resetting the bios. You'll have to check your manual for how to do this. Some have an option in the setup screen, others require changing a jumper on the MoBo. Anyway, that where I'd look.

Thanks for that. Thats not what i wanted to hear lol. Ill give it a try once i get a chance.

---

### Post by kelvin spratt on 2007-06-01
Before you do anything boot up xp go to control panel, administration, disc manager, your drive should show there make sure its activated you should have done that when you installed it, you might have to format it to activate it. once activated it will be recognized in bios, as it sounds as its still a raw drive

---

### Post by Patrick K on 2007-06-01
Even an unformatted drive will show up in the bios. The bios doesn't care if it is formatted. It reads the raw data the mfg provides in firmware. The bios doesn't depend on any OS to activate or provide any info to it. 

To the OP, you might try unplugging and re-plugging the cables (both power and data, do both ends) for the drive. Check that they are fully seated.

---

