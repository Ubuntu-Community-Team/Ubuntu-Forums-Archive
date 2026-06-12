---
title: "Visual effects help"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by jprice19 on 2008-03-25
For some reason it won't let me switch my visual effects from none. My computer is only about a year and a half or so old. It just says desktop effects could not be enabled. Is there something I have to change before I can do that? I'd really appreciate some help. I'm really new to this so I'm trying to learn.

---

### Post by overdrank on 2008-03-25
> **jprice19 said:**
> For some reason it won't let me switch my visual effects from none. My computer is only about a year and a half or so old. It just says desktop effects could not be enabled. Is there something I have to change before I can do that? I'd really appreciate some help. I'm really new to this so I'm trying to learn.

Hi and welcome, what is the model of the graphics card? You can find this with the command in the terminal  lspci. The terminal is located under applications, accessories. Look for VGA.
Edit and also what are the system specs like memory.

---

### Post by jprice19 on 2008-03-25
• AMD Turion™ 64 and Mobile Sempron™ Processors
• 12.1" WXGA Display Supporting up to 1280x800 Hi-def Resolution
• 512MB or 1GB System RAM Upgradeable to 2GB
• 80GB Hard Drives
• VIA K8N890 Integrated Graphics

sorry it took a while. i lost my connection. it copied this from the website

---

### Post by forrestcupp on 2008-03-25
> **overdrank said:**
> Hi and welcome, what is the model of the graphics card? You can find this with the command in the terminal  lspci. The terminal is located under applications, accessories. Look for VGA.
Edit and also what are the system specs like memory.

Yeah, we need to know what kind of video card you have and which drivers you have installed.  The easy way to get the one line you need from lspci is to type in a terminal
```
lspci | grep VGA
```
That will give you the one line that tells you your video card.

---

### Post by overdrank on 2008-03-25
> **jprice19 said:**
> • AMD Turion™ 64 and Mobile Sempron™ Processors
• 12.1" WXGA Display Supporting up to 1280x800 Hi-def Resolution
• 512MB or 1GB System RAM Upgradeable to 2GB
• 80GB Hard Drives
• VIA K8N890 Integrated Graphics

sorry it took a while. i lost my connection. it copied this from the website

Hi and please correct me but I believe that is unichrome 
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by BL00dFox on 2008-03-25
Are your restricted drivers enabled?

---

### Post by jprice19 on 2008-03-25
VIA Chrome 9™ IGP (Integrated Graphics Core)   K8M890CE

I apologize for having no idea what's going on lol.

---

### Post by jprice19 on 2008-03-25
it said I didn't need any restricted drivers

---

### Post by iSplicer on 2008-03-25
Run

```
glxinfo
```

and post output here please

---

