---
title: "Codec for Totem?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by grissjuk on 2007-11-04
Hello,
I'm new here, and I'm pretty unfamiliar with Linux. 

I'm currently trying Ubuntu and having problems with getting things to WORK, so I can do some WORK. When I'm looking at the response newcomers get here, I get sceptical. Advanced user demand that the newcomers know how to ask the right questions, but the problem, you see, is that we know too little to actually know what we don't know and how to ask correctly. THEREFOR the initial questions will have to be a dialectic process, where you can guide the newcomer in the right direction. Scorn DOES NOT help that process.

So to my question:
I can't play DVDs on my Totem player. It asks for plugins. I've read some about plugins and codec, but still struggle to find a spesific codec/plugin that I can download. Can anyone help me?

---

### Post by Incense on 2007-11-04
Follow the directions on this page to get your DVDs working. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Maestro23 on 2007-11-04
> **grissjuk said:**
> Hello,
I'm new here, and I'm pretty unfamiliar with Linux. 

I'm currently trying Ubuntu and having problems with getting things to WORK, so I can do some WORK. When I'm looking at the response newcomers get here, I get sceptical. Advanced user demand that the newcomers know how to ask the right questions, but the problem, you see, is that we know too little to actually know what we don't know and how to ask correctly. THEREFOR the initial questions will have to be a dialectic process, where you can guide the newcomer in the right direction. Scorn DOES NOT help that process.

So to my question:
I can't play DVDs on my Totem player. It asks for plugins. I've read some about plugins and codec, but still struggle to find a spesific codec/plugin that I can download. Can anyone help me?

Welcome to Ubuntu man.  Start with Restricted Formats and the Medibuntu Page:
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Goshawk on 2007-11-04
totem use gstreamer lib and is not able to play dvd menu as well.

install the libdvdcss3 package then do:
/usr/share/doc/libdvdread3/examples/install-css.sh

now install vlc and you will be able to play dvds with menu

---

### Post by grissjuk on 2007-11-05
> **Goshawk said:**
> totem use gstreamer lib and is not able to play dvd menu as well.

install the libdvdcss3 package then do:
/usr/share/doc/libdvdread3/examples/install-css.sh

now install vlc and you will be able to play dvds with menu

Thank you very much, but where do I find the libdvdcss3? And how do I install it?

---

### Post by grissjuk on 2007-11-06
Where do I find the libdvdcss3? And how do I install it?

---

