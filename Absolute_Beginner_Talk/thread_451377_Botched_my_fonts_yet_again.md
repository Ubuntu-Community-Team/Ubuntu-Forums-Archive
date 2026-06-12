---
title: "Botched my fonts yet again"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-22
[B]Edit: I was not able to resolve this issue. The only way I could get rid of it was by reinstalling Ubuntu. 
[/B]
So, it's official. I've botched my Ubuntu installation yet again. 

For yet another round, it seems that my fonts have gone chaotic. Sometimes, upon rebooting, they'll become utterly fuzzy.  And at other times, my fonts look very stretched(even more stretched than my fonts in my screenshots look like).

What possibly caused this problem:

I'd just done a fresh install of Ubuntu and thus, pasted my copy of fonts.conf into /home/<user> after I'd installed mlind's patches. And then, everything went bonkus after I restarted X. 

Here're all the steps I've attempted:

a) copied fonts.conf into Root folder. That worked for a while. And then, everything went chaotic again after which I tried removing certain entries in font.conf. Nope, that didn't work either so, I deleted fonts.conf from Root. 

b) blanked out various settings in fonts.conf from my /home/user folder.

c) reset xorg.conf by manually selecting monitor and graphics card. I did this many times. 

d) reset fontconfig many times. 

e) also tried purging fontconfig by using these commands:

sudo dpkg --purge --force-all fontconfig-config

and  sudo apt-get install fontconfig-config

f) Am using mlind's method and have uninstalled and reinstalled the patches many times over. 

That is, the following patches have been reinstalled and uninstalled many times over: libfreetype6 libcairo2 libxft2 

g) I just tried deleting fonts.conf from /home/<user> and also deleting fonts.conf from Root folder. Interestingly enough, my preset font configurations were still loaded. 


Included are a few screenshots detailing my problem:

1) In Firefox and even Opera, the Monotype font looks a little stretched. Though sometimes, the fonts become this huge mess of glowing fonts with absolutely fuzzy edges or look like they're melting:

[[IMG]http://img525.imageshack.us/img525/1032/oddfonts1ps8.th.png[/IMG]](http://img525.imageshack.us/my.php?image=oddfonts1ps8.png)


2) This is what my Monospace font looks like in Text Editor and many other applications like Terminal, etc.:
[[IMG]http://img265.imageshack.us/img265/2955/oddfonts2dk6.th.png[/IMG]](http://img265.imageshack.us/my.php?image=oddfonts2dk6.png)

3) This is what my Sans Serif font @ size 12 looks like in Konqueror. At present, my fonts in Nautilus  and other applications look a little stretched but sometimes, they get even err... longer?

[[IMG]http://img151.imageshack.us/img151/9446/sansserif1bp7.th.png[/IMG]](http://img151.imageshack.us/my.php?image=sansserif1bp7.png)

Right now, I'm at my wit's end. So, anyone knows how to purge all my font settings so I can start anew?

---

### Post by freakboysystem on 2007-05-22
the fonts in the pictures look fine.

---

### Post by Lucifiel on 2007-05-23
They may look fine but actually they didn't. 

I finally managed to make most of the problems go away but $#%$#%$#%, forget it. It's time to go back to Windows XP.

---

### Post by kenthomson799 on 2007-06-02
> **Lucifiel said:**
> ...I finally managed to make most of the problems go away but $#%$#%$#%, forget it. It's time to go back to Windows XP.
You could have  written what you did to get you back to normal (or almost normal) condition.
That would have helped someone like me. Once you start a thread it becomes your responsibility to mark it "Resolved" and post the answer as your last message.

---

### Post by Lucifiel on 2007-06-03
> **kenthomson799 said:**
> You could have  written what you did to get you back to normal (or almost normal) condition.
That would have helped someone like me. Once you start a thread it becomes your responsibility to mark it "Resolved" and post the answer as your last message.

Well, I simply reinstalled Ubuntu and that was not really a solution.

And so? I don't owe you anything. I simply forgot about this thread and using terms like "it becomes your responsibility" is just what? totally nuts? Please freaking realise I've got a life out there, you know?

---

