---
title: "basic desktop"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by redhue on 2007-11-17
how do i get back to the basic ubuntu graphical desktop you know the newby friendly one?

---

### Post by rsambuca on 2007-11-17
What were you doing just prior to losing your graphical desktop?  Were you trying to install programs, etc?

What happens when you boot up now - do you get error messages, or just a command line prompt?

---

### Post by redhue on 2007-11-17
> **rsambuca said:**
> What were you doing just prior to losing your graphical desktop?  Were you trying to install programs, etc?

What happens when you boot up now - do you get error messages, or just a command line prompt?

i get a rectangle box asking for user name. and the password. which is all fine and then it takes me to what I think is nautilis which gives me a list of files and such to select.ve stubled threw this blindly until I finaly got on line and carefully brought me  here but  i have none of the icons onthe top right to minimize or close or maximize so far ubuntu has been great to me but i made the mistake of braggng about how much better and safer it was than microsoft and i allowed a freind to mess around wth it so they culd see what i meant and now here i am

---

### Post by redhue on 2007-11-17
actually im afraid to close this window at this point because im not sure how i got here so i dont know how to get back even if i could figure out how toreboot without turning off the machine other than hitting the reset

---

### Post by rsambuca on 2007-11-17
Try pressing Alt-F2 to get an application launcher.  The enter 'gnome-terminal' to get a terminal window.

Then enter 'gnome-panel' and see if that helps launch one.  If it does, you can manually set the panels back up.  

Let us know if this works.

---

### Post by Inxsible on 2007-11-17
it seems you have lost your window borders. Once you pull up a terminal, you might also wanna try reloading compiz if you use it or metacity
```
metacity --replace
```

---

### Post by redhue on 2007-11-17
nothing happened with altF2 and i have no idea what isa meant by compiz. sorry your dealing with a true novice here but i do appreciate your help and patience but you wil probably have to walk me threw this in baby steps treat me as if im really stupid no offence will be taken thankyou

---

### Post by Inxsible on 2007-11-17
**Again, I am trying to clarify here**
You are holding down Alt and then pressing F2 right ?

---

### Post by redhue on 2007-11-17
yes what should be happening

---

### Post by Inxsible on 2007-11-17
it should pull up a run dialog wherein you would enter the command that rsambuca gave you to start the gnome-panel again.

---

### Post by zabien1970 on 2007-11-17
Can you access the terminal, top left corner

Applications>Accessories>Terminal

---

### Post by redhue on 2007-11-17
no top left of this window  have File, Edit,View,History,Bookmarks,Tools,Help

---

### Post by redhue on 2007-11-17
I would like to get back to where I have Applications,Places,System on the top left again

---

### Post by Inxsible on 2007-11-17
> **redhue said:**
> no top left of this window  have File, Edit,View,History,Bookmarks,Tools,Help

> **redhue said:**
> I would like to get back to where I have Applications,Places,System on the top left againmore and more i feel that you probably just lost the window borders. If you have set up a shortcut for the terminal try that to pull it up. What happens when you press Alt + F2 ? the run dialog doesn't come up ?

Alternatively, Try and reboot again, that would fix it sometimes.

---

### Post by zabien1970 on 2007-11-17
Inxsible  in his third post he said he did reboot, I'm afraid if we have him do it again we may lose him

  Redhue if you put your mouse all the way to the left can you grab the window and drag it over to the middle to see whats behind it, then if someone knows the keyboard shortcut to take a screenshot we can see where you are, I'm not an expert myself but this may help us

---

### Post by redhue on 2007-11-17
hey im back whew that was close i thought i was never going to make it back. any way i figured out how to get back her. how do i show you guys the screen that i have behind this one

---

### Post by redhue on 2007-11-17
nothing happens with Alt-F2 that i can tell. and when i tried to use my mouse and press the left button to drag it wouldnt move the window.then i saw a little bit of what appeared to be aportion of a window hanging out on the right side so i clicked on that is there any way that i can display it to you so you can tell me what to do with that

---

### Post by redhue on 2007-11-17
ok here goes detailed description top bar has File,Edit,View,Go,Bookmarks,Help. Then the bar below that has an arrow < and below that the word BACK. Next an arrow points > and below that the word FORWARD.And then same arrow pointing up with the word UP below that. Then a circle with an X and the word STOP. After that is 2 arrows onthe word RELOAD below that. more icons but the words are HOME,COMPUTER,SEARCH.Next bar there is the icon with the paper and pencil inside of a grey box.After which the word Location: and then there is a line that reads exactly as follows /home/redhue/Desktop.At theend of that line there are the magnifing glasses with the+and- signs and a 25% between them after which it readsView as List inside of a gray box. there is more should i go on?

---

### Post by schauerlich on 2007-11-17
Is this all you can see on the screen? Is there a desktop behind it, or a bar above File,Edit, View etc?

---

### Post by avik on 2007-11-17
> **redhue said:**
> ok here goes detailed description top bar has File,Edit,View,Go,Bookmarks,Help. Then the bar below that has an arrow < and below that the word BACK. Next an arrow points > and below that the word FORWARD.And then same arrow pointing up with the word UP below that. Then a circle with an X and the word STOP. After that is 2 arrows onthe word RELOAD below that. more icons but the words are HOME,COMPUTER,SEARCH.Next bar there is the icon with the paper and pencil inside of a grey box.After which the word Location: and then there is a line that reads exactly as follows /home/redhue/Desktop.At theend of that line there are the magnifing glasses with the+and- signs and a 25% between them after which it readsView as List inside of a gray box. there is more should i go on?

Okay, so that's the Nautilus/File Manager window.  Is that *all* that's on the entire screen, or is there a background or something else besides the File Manager window?

---

### Post by redhue on 2007-11-17
if i go to the drop down menu of File on that page iget the desktop solid color background and ther are icons of files down the left side and also a picture of the GIMP but that is all there is on the whole screen until iclick on one of the file icons the i either get the window previously described and if i click on another i get my uneployment online application from afew months ago and navigate back here from that point

---

### Post by schauerlich on 2007-11-17
Are you on a laptop? If so, you may have to press Fn+Alt+F2 to get to the "Run" dialog. Then type in 

```
metacity --replace
```

And press enter.

---

