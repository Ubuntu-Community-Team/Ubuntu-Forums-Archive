---
title: "Reinstalled Amarok, lost mp3-support"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-21
What the title says. :)

I removed Amarok completely, for a few different reasons, and when I reinstalled it seems to have lost its ability to play mp3s. Between uninstalling and reinstalling I ran the kernel update, and now I am wondering if that is what caused it, and if I will have to do the "restricted formats" tweak through that long tutorial in another forum, every time I do a kernel update?

I'm sure I am capable of that, but if that's the case I do wish someone had told me so I could have planned for it.

/Mimsy

---

### Post by mitch.c on 2006-09-21
> **Mimsy said:**
> I removed Amarok completely, for a few different reasons, and when I reinstalled it seems to have lost its ability to play mp3s.
Is libxine-extracodecs installed?

> **Mimsy said:**
> Between uninstalling and reinstalling I ran the kernel update, and now I am wondering if that is what caused it, and if I will have to do the "restricted formats" tweak through that long tutorial in another forum, every time I do a kernel update?

No, you shouldn't have to go through this. I've never had a problem like this. When you un installed Amarok, libxine may have been removed (assuming that's what's missing).

---

### Post by Mimsy on 2006-09-21
I think libxine-extracodecs is installed. When I searched the forums for a solution earlier tonight I found a post that suggested installing that package, so I did, with sudo apt-get. Amarok still won't play my mp3s though, so I'm thinking maybe it's not fully installed, or some dependencies are missing.

And I'm glad to hear this is not typical. With the problems I have with battery life on the laptop, I was starting to think Ubuntu was not for me after all... and I like it, and would have been very unhappy to have to go back to Windows. I still have to find a way to make the battery last longer, though.

/Mimsy

---

### Post by mitch.c on 2006-09-21
> **Mimsy said:**
> I think libxine-extracodecs is installed. When I searched the forums for a solution earlier tonight I found a post that suggested installing that package, so I did, with sudo apt-get. Amarok still won't play my mp3s though, so I'm thinking maybe it's not fully installed, or some dependencies are missing!
What version is Amarok? Are you using 1.3.9? If so, you might try 1.4.3. I helped someone else through a problem like this recently, and switching to 1.4.3 took care of everything. It's rock solid.

Try this: [http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/](http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/)

---

### Post by Mimsy on 2006-09-21
According to my installation of Amarok, it's version 1.4.2.

Reinstalling libxine-extracodecs through Synaptic solved it!

Thanks! :D

/Mimsy

---

