---
title: "Ubuntu beryl installed! Help configure"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Sale 666 on 2007-09-24
Well now that i installed my nvidia 8800gtx and all works fu+ine i instaled beryl with the pacage now i got under system beryl manager and theme emrald bu i cannot use the effects nothing is actualy showing what ever i do i see no effects! i change stuff under the emerald and beryl manager... am i mising something here?  thanks!

---

### Post by overdrank on 2007-09-24
> **Sale 666 said:**
> Well now that i installed my nvidia 8800gtx and all works fu+ine i instaled beryl with the pacage now i got under system beryl manager and theme emrald bu i cannot use the effects nothing is actualy showing what ever i do i see no effects! i change stuff under the emerald and beryl manager... am i mising something here?  thanks!

Hi I am glad to see you stuck it out with ubuntu. If you have a red diamond on the top panel then you can right click it and choose beryl as the window manager. Good luck! :popcorn:

---

### Post by Sale 666 on 2007-09-24
[[IMG]http://img398.imageshack.us/img398/2697/screenshotlt6.png[/IMG]](http://imageshack.us)

here is how far i got and thats all...
i got no diamond :( .. aww
what should i do now? can you give me  a hint what to do?

---

### Post by overdrank on 2007-09-24
Under applications, system tools  beryl manager and click it or use the key alt,F2 and type in beryl-manager and this will activate beryl.
Then if it works good and no problems you can add it to the start up under system,preference,sessions and create a new one with the same command.

---

### Post by Sale 666 on 2007-09-24
i got a problem says cannot find file///beryl-manager
uh... maybe i installed it wrong? how can i make you some kind of log file?

---

### Post by overdrank on 2007-09-24
> **Sale 666 said:**
> i got a problem says cannot find file///beryl-manager
uh... maybe i installed it wrong? how can i make you some kind of log file?

Try this command in the terminal
```
sudo apt-get install beryl-manager beryl emerald-themes
```

---

### Post by Sale 666 on 2007-09-24
ok thanks it works now i got the diamond but its all wierd i dont have cube i got 1 desktop and if i go left or right with a window it goes to black! and sometimes like its got a mind of its on goes back like zooms out of my window! and firefox shrinks to a thin line and i cant maximize it anymore! is there any way to resert all to defaults? cause i was trying out effects when beryl didnt work but nothing did happen so it is all on with effects... oh... i messed up!

---

### Post by Sale 666 on 2007-09-24
how do i add back my desktops? cause in right lower corner is only 1 now! and i want to make a cube of 4 desktops and the background picture when looking at the cube

---

### Post by Sale 666 on 2007-09-24
can some 1 tell me the code so i can totoaly remove beryl! and stay on gnome... 
than reinstall it!

Please provide codes to uninstall than reinstall!

Thank you!

---

### Post by overdrank on 2007-09-24
> **Sale 666 said:**
> can some 1 tell me the code so i can totoaly remove beryl! and stay on gnome... 
than reinstall it!

Please provide codes to uninstall than reinstall!

Thank you!

```
sudo apt-get remove beryl-manager beryl emerald-themes
```
Then go to synaptic manager and search for beryl to make sure all is removed

---

### Post by Sale 666 on 2007-09-24
ok i made it! removed and now works fine but here is the problem i cant manage the effects to work! can you help me here? i chose the effects i want but not showing!
heres the screen shoot
[[IMG]http://img223.imageshack.us/img223/2135/screenshotzt5.png[/IMG]](http://imageshack.us)
i highlighted the effects i want but not workin... do i need to activate it somehow? thanks...
also i cannot see the cube to zoom out of it i can only turn it on desktops...

---

### Post by Sale 666 on 2007-09-24
[http://www.youtube.com/watch?v=ZD7QraljRfM&mode=related&search=](http://www.youtube.com/watch?v=ZD7QraljRfM&mode=related&search=)
could you look at this please and tell me whats the top bar called that he got!

---

### Post by overdrank on 2007-09-24
> **Sale 666 said:**
> [http://www.youtube.com/watch?v=ZD7QraljRfM&mode=related&search=](http://www.youtube.com/watch?v=ZD7QraljRfM&mode=related&search=)
could you look at this please and tell me whats the top bar called that he got!

Could be kiba-dock
[http://www.kiba-dock.org/](http://www.kiba-dock.org/)

---

### Post by Sale 666 on 2007-09-24
thanks! 
And 1 more and last thing about this :D

How do i make the effects work and how do i make the cube visible? so i can zoom the cube out!

---

### Post by overdrank on 2007-09-24
use the keys ctrl,alt, and single click with the mouse and there you go

---

### Post by Sale 666 on 2007-09-24
awsome! thanks! o ye how can i make it transparent? and i downloaded the kiba dock but i dont know how to use it! it isnt showing! lol sorry for bothering you with a lot of questions!

---

### Post by overdrank on 2007-09-24
> **Sale 666 said:**
> awsome! thanks! o ye how can i make it transparent? and i downloaded the kiba dock but i dont know how to use it! it isnt showing! lol sorry for bothering you with a lot of questions!

Transparent is in the beryl settings manager under desktop cube I believe and as for kiba dock I can not help there. Good luck!

---

### Post by Sale 666 on 2007-09-24
ok i found it and tried but not working... never mind ill keep trying! 
Do you maybe know how do make the fire effects work? you know when you open the drop down menu and go away it burns... i found it but its also not working!
:(

---

### Post by Maestro23 on 2007-09-24
> **Sale 666 said:**
> ok i found it and tried but not working... never mind ill keep trying! 
Do you maybe know how do make the fire effects work? you know when you open the drop down menu and go away it burns... i found it but its also not working!
:(

Might answer some of your questions: [http://www.beryl-project.org/faq.php](http://www.beryl-project.org/faq.php)

---

### Post by Sale 666 on 2007-09-24
ok now beryl wont start again i right click on the beryl icon and chose select window manager beryl and it doesnt wont to it goes back to gnome!...
EDIT: ok i removed beryl and installed again and its working again! but how do i make it start up? and make it transparent? the transparent under desktop cube does not work

---

