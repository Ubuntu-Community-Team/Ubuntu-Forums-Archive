---
title: "major beryl problems"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-01-24
well i installed beryl according to some instructions on this forum.  and at the end of the instrucctions it said to press Control + ALT + Backspace.  well i did and it gave me an error and than there was a black screen with a flashing curser on it.  now i cant even get into ubuntu.  it keeps giving  me errors with GDM i believe.  the error says "fatal server error   no screen found"

what in the world did i do and how do i fix it.  i can load the recovery mode from grub but i dont know what to do.  its like it automatically tries to start beryl when i turn the computer on.  my cd-rom doesnt even read a new ubuntu live cd or install cd.  please help me....this sucks and i dont know what to do.  thank you so much

---

### Post by jbayone on 2007-01-24
I had a similar problem.  In recovery mode I think I just removed beryl, then restarted x.  Maybe someone else has a better solution since I was never able to get beryl working.

---

### Post by Happy_Man on 2007-01-24
Yea, that happened to me too. I waited for a bit, and then gave up and turned off the computer manually. Then I waited 30 seconds and turned it back on. Problem solved (for me anyway)!

---

### Post by dragnazz5.0 on 2007-01-24
well if i could figure out how to get rid of beryl on the recovery mode than that would be great but im not that linux savvy yet.  and i probably turned my computer off and on 30 times today trying to get it to work and it doesnt.

---

### Post by jbayone on 2007-01-24
I think it's sudo aptitude remove beryl, something like that

---

### Post by Shatrat on 2007-01-24
I'm not sure which guide to beryl you used, but i like
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

While you're going through the process check your work.  Make sure you have direct rendering.  Start up with XGL and Gnome before trying XGL and Beryl, et cetera.
Remember, Beryl is very much beta software still, even though it is making great progress.

---

### Post by NewOldTimer on 2007-01-24
Dragnazz5.0, 
    So sorry to hear your still having problems. I'm way to much of a noob to help with your current problem but if your original problem came from the link I referd you to, you may need to double check your steps{ if your concidering even trying again}.
    I had to read and re-read the page twice to follow "all" the step's in sequence PERTAINING to MY set-up{intel}. I also ran the code to add lupine'skey for the "Latest" beryl.
    Once again I'm sorry you may have gotten into this mess on my account, But I'm sure there's someone out there with vast more knowledge than what I can offer... Good Luck

---

### Post by dragnazz5.0 on 2007-01-25
> **NewOldTimer said:**
> Dragnazz5.0, 
    So sorry to hear your still having problems. I'm way to much of a noob to help with your current problem but if your original problem came from the link I referd you to, you may need to double check your steps{ if your concidering even trying again}.
    I had to read and re-read the page twice to follow "all" the step's in sequence PERTAINING to MY set-up{intel}. I also ran the code to add lupine'skey for the "Latest" beryl.
    Once again I'm sorry you may have gotten into this mess on my account, But I'm sure there's someone out there with vast more knowledge than what I can offer... Good Luck

hey man, no you had nothing to do with my problem.  im sure i just screwed something up.  thank you for the help and the links.  

i finally figured out how to get my cd to read and i had to reinstall ubuntu.  now i have to redo all my bookmarks and settings.  but first im gonna upgrade to edgy.  than im gonna find the right instructions for beryl.  it took me so long to figure out how to do anything through sudo aptitude since im such a newb.  but i figured it out.  so hurray for me.  well lets see how this goes.

---

### Post by dragnazz5.0 on 2007-01-28
alright, everytime i try to get beryl to work my computer screws up and i have to reinstall linux.  its really pissin me off.  i dont understand why it wont work.  i do everything that the instructions say.  last time i installed beryl and i tried to run beryl manager i got this error:

beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
Edit/Delete Message

i dont understand what in the world im doing wrong...if im doing anything wrong.  when my computer screws up is when i try to reboot it and i get an error that says "no screen found"

---

### Post by Waappu on 2007-01-28
Hi

If you can try to use AiGLX. I think it's more easy to get working. What video card you have ?

---

