---
title: "I need a bit of help"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Kem Rixen on 2005-12-07
I'll start with a little story about how I got to this point. I'd heard about linux a while ago, used it, I thought I could handle it. I glanced at some of the tutorials and such and thought, it couldn't be too hard. Well, I came from Windows XP which is very simplistic, it's quite a change. Now to the quite pathetic question I have. How do I install a program? I tryed to install wine following [this](http://www.winehq.org/site/download-deb) tutorial and got horribly lost.

Any help with my cluelessness would be greatly appreciated as I really want to use linux.

---

### Post by aysiu on 2005-12-07
See the second link in my sig.

---

### Post by Kem Rixen on 2005-12-07
I'm sorry if I'm so slow and stupid but, what's a terminal and how do I get to it?

---

### Post by aysiu on 2005-12-07
[QUOTE=Kem Rixen]I'm sorry if I'm so slow and stupid but, what's a terminal and how do I get to it?[/QUOTE] If you're in Breezy (the latest version--5.10), go to Applications > Accessories > Terminal. If you're in Hoary (version 5.04), go to Applications > System Tools > Terminal.

---

### Post by teaker1s on 2005-12-07
it's under applications-system tools gnome terminal(looks like tv icon)
or hit add applications and advanced or terminal 'sudo synaptic'
change preferences to recommended packages as dependencies.
search away games etc etc or look through sectionsclick and install

---

### Post by chilebeans on 2005-12-07
Kem


Go to my post started under "Network Configurations", than click on page 12.....I am learning but getting there..So far I should have installed a program called Gizmo but now I need to upgrade my version from 5.04 to the newest one.

Just read the post conversation.........it will be extremely helpful I think because thats what I am learning.

---

### Post by chilebeans on 2005-12-07
Kem

Correction...look at page 13 I mean.....and start reading from where I say "Gizmo"....its a talking program on the internet. Its about half way down page 13

---

### Post by Kem Rixen on 2005-12-07
I opened up the terminal and typed in ```
sudo apt-get install wine
``` It asked for my password, I tryed to type it in but I couldn't.

---

### Post by aysiu on 2005-12-07
[QUOTE=Kem Rixen]I opened up the terminal and typed in ```
sudo apt-get install wine
``` It asked for my password, I tryed to type it in but I couldn't.[/QUOTE] Sure you could. It just doesn't appear to register--there'll be no **** signs or any kind of visual feedback that you've entered it, but you can enter it, then press **Enter**.

---

### Post by YokoZar on 2005-12-08
You could have done this without the terminal by using Synaptic (System->Administration->Synaptic Package Manager).

Perhaps I should update that page...

---

### Post by Kem Rixen on 2005-12-08
Ok, I did it typed in my password and it told me that wine wasn't availible and that I'd need to get it somewhere else. So, now what do I do?

---

### Post by carlosqueso on 2005-12-08
hmmmm...you probably haven't enabled the Universe and Multiverse repositories.

Follow these directions to do it: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

then try it again.

---

### Post by Kem Rixen on 2005-12-08
Hooray, that worked, now hopefully the final question, where did it install it, how do I run it?

---

### Post by Qrk on 2005-12-08
to run it type

```
wine *windowsprogram*
```

into a terminal. You'll have to configure it first, though. Type 

```
winecfg
```

into a terminal.

Edit: A hint... Linux programs aren't installed to "wheres" like in windows. You don't have one directory for a program, different parts of a program are broken into different directories. Look for wine in /usr/share/wine.

---

### Post by Kem Rixen on 2005-12-09
I read through a lot of the things on wine's website and still can't figure out how to install a windows program with wine. I think I might have done it already but I'm really not sure and I can't find any folders in wine that could prove that I installed it.

---

