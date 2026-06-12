---
title: "Viruses?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by petgraveyard on 2006-06-28
I'm wondering something about viruses...I just got sent an email virus in Hotmail (obviously, about 1000 gifs were attached to it, and the pictures were of nothing), and I scoffed.  However, this led me to wonder something - is it possible for a sort of virus or something on Ubuntu?  How would we defend ourselves?  Is it possible that that virus I got in Hotmail could have infected my Ubuntu install (I'm laughing at the thought)?

---

### Post by jrd on 2006-06-28
I'm a little new to linux so someone correct me If i'm wrong.....
At the moment there are no linux viruses in the wild. So the ones you got are pretty much just sitting there, however, if you network with windows computers you could infect them.

---

### Post by petgraveyard on 2006-06-28
I just thought of something.

How could I get a virus looking at just gifs, even on Windows?  I don't think I could based on these things:
a.) Incoming files to Hotmail are scanned by Trend Micro
b.) I never downloaded and "executed" them, I just looked at them

I think I might know what it is!  I'm sure everyone knows about that Windows exploit where some sort of code execution occours from images.  That might be what I got!

---

### Post by jrd on 2006-06-28
Good thing you don't use windows!;)

---

### Post by petgraveyard on 2006-06-28
I use it sometimes (I'm still getting all of my stuff over to Ubuntu), but I guess it's a good thing I wasn't using it at that time!

---

### Post by nalmeth on 2006-06-28
I'm no expert on the subject, but merely by opening (looking) a file with malicous code will execute the malicous code through a security hole in the facilitating application, in this case, the browser, IE.

This code was designed for windows, and could only run because IE will have full priviledges to run anything.

Conversely, for ubuntu, even if the code was designed with linux binaries in mind, firefox does not have permission to alter files or folders outside of /home.

It's the security model that you benefit from with linux, and on top of that, security patches are released incredibly fast when vulnurabilities are discovered. 

Your bases are quite covered. Just don't be tricked into giving your user password.

---

### Post by ProjectGod on 2006-06-28
hmmm viruses. most of the viruses i've come across were either, zip files, .vbs files, .exes, .bat, .com, .dll... they cause chaos on my windows machines by editing the registry, faking valid system files etc

i dont think the virus written for windows (99.9% of viruses) can infect a linux system... for one thing these viruses are system architecture specific... they do not mutate or evolve like real viruses that infect living organisms.

hey but what do i know? i guess you could try to install symantec on your linux. :lol:

---

### Post by djsroknrol on 2006-06-28
If you're really worried about viruses, you could try clamAV or AVG has a Linux version

---

