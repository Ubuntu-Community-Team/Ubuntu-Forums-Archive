---
title: "How to get rid of black lines when maximising/minimising"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by mason215 on 2008-02-15
good now that i have your attention i have question whenever i minimize or maximize a window there are black bars is there any way to get rid of these without using compiz-fusion.
heres a pic of a window minimizing

[http://img155.imageshack.us/img155/6...hotcopyqp9.png](http://img155.imageshack.us/img155/6...hotcopyqp9.png)

thanks

---

### Post by stevejesus on 2008-02-15
That link appears to be broken.

---

### Post by MNICY on 2008-02-15
Your image is not appearing.

---

### Post by stchman on 2008-02-15
> **mason215 said:**
> good now that i have your attention i have question whenever i minimize or maximize a window there are black bars is there any way to get rid of these without using compiz-fusion.
heres a pic of a window minimizing

[http://img155.imageshack.us/img155/6...hotcopyqp9.png](http://img155.imageshack.us/img155/6...hotcopyqp9.png)

thanks

Try reposting your screenshot.

---

### Post by dje on 2008-02-15
I assume mason215 means the black bars that follow windows after they have been minimized to the gnome panel?

You can disable this by running gconf editor:
```
gconf-editor
```
Then naviagate to apps >> metacity >> general
Then tick reduced_resources

Bear in mind this will also turn off showing window contents while dragging and I think this is the only way to do it

Hope that helps
dje

---

### Post by PriceChild on 2008-02-15
Every time someone posts with a useless title, a moderator kills a kitten.

Seriously now... decent titles make it easier for future users to find this thread if they have a similar problem.

---

### Post by mason215 on 2008-02-15
> **PriceChild said:**
> Every time someone posts with a useless title, a moderator kills a kitten.

Seriously now... decent titles make it easier for future users to find this thread if they have a similar problem.

i am not saying i wanted to do this, but after i had posted this subject 2 times and no one responded and then bumped both of them after an hour. What was i supposed to do. And just for measure in those 2 threads no one even viewed. So next your reply something, you should think where i am coming from.

---

### Post by mason215 on 2008-02-15
> **dje said:**
> I assume mason215 means the black bars that follow windows after they have been minimized to the gnome panel?

You can disable this by running gconf editor:
```
gconf-editor
```
Then naviagate to apps >> metacity >> general
Then tick reduced_resources

Bear in mind this will also turn off showing window contents while dragging and I think this is the only way to do it

Hope that helps
dje

thanks that fixed the problem

---

### Post by stchman on 2008-02-15
You mean this was a thread about removing the 0.2sec animation that happens during maximize and minimize?

---

### Post by mason215 on 2008-02-15
> **stchman said:**
> You mean this was a thread about removing the 0.2sec animation that happens during maximize and minimize?

yeah, it was bothering me

---

### Post by stevejesus on 2008-02-15
lol.
But... in your defense... it is pretty ugly.

---

### Post by stchman on 2008-02-15
> **mason215 said:**
> yeah, it was bothering me

It is BARELY noticeable.  You ahve to look real hard for that 0.2 seconds to even notice.  I was under the impression that you had black lines running across your screen.  Between the title and purpose that was a really useless thread.

---

### Post by mason215 on 2008-02-15
> **stchman said:**
> It is BARELY noticeable.  You ahve to look real hard for that 0.2 seconds to even notice.  I was under the impression that you had black lines running across your screen.  Between the title and purpose that was a really useless thread.

yeah i guess i am a perfectionist, but they are ugly.

---

### Post by erginemr on 2008-02-15
Don't worry, those lines were also bothering me, and this is one of the reasons why I switched on desktop effects.

Whatever, "apps >> metacity >> general >> tick reduced_resources" as proposed above is correct, to which I had also resorted. But in my experience, that has left a nasty side effect; a mesh of black lines when moving windows. 

To get rid of that one as well, I went to "Main Menu >> System >> Preferences >> Universal Access >> Assistive Technology Preferences" and ticked "Enable Assitive Technologies" and this trick has eliminated the mesh.

---

### Post by mason215 on 2008-02-15
> **erginemr said:**
> Don't worry, those lines were also bothering me, and this is one of the reasons why I switched on desktop effects.

Whatever, "apps >> metacity >> general >> tick reduced_resources" as proposed above is correct, to which I had also resorted. But in my experience, that has left a nasty side effect; a mesh of black lines when moving windows. 

To get rid of that one as well, I went to "Main Menu >> System >> Preferences >> Universal Access >> Assistive Technology Preferences" and ticked "Enable Assitive Technologies" and this trick has eliminated the mesh.

i dont seem to have universal access, do i have to download it?

---

### Post by erginemr on 2008-02-16
No, it is disabled / hidden by default. Right click on the Ubuntu main menu, select "edit menus", go down to System -> Preferences, tick the checkbox beside "Universal Access" and close it. Then from the Main Menu -> System -> Preferences -> Universal Access, select "Assistive Technology Preferences". And activate the a/m checkbox.

However, if you have gotten rid of the minimize/maximize lines by editing the respective setting in gonf-editor as mentioned before, and do not happen to observe a grid when you move windows, then you do not need to apply this trick.

---

### Post by erginemr on 2008-03-17
Hello again **mason215**,

The new version of metacity (to be implemented in Hardy) supports basic compositing such as drop-shadows under windows and menus. It also replaces the lines shown during minimize and maximize with a better animation.

So, if you are not currently using Compiz, you can give the new metacity compositor a try by following the thread:
[http://ubuntuforums.org/showthread.php?t=648364](http://ubuntuforums.org/showthread.php?t=648364)

and downloading and installing the three debian packages given by the OP.

---

