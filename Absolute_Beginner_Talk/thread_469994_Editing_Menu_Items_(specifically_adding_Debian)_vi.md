---
title: "Editing Menu Items (specifically adding Debian) via alacarte"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Kale Tainer on 2007-06-10
This seems to be a popular problem, but I have yet to find a solution that works for me.

Problem: Editing Menu Items (specifically adding Debian) via alacarte. 

Tried: Right-click on the panel and edit menus -> clicking on checkbox by Debian to add it Result: nothing happens and the next time i bring up edit menu Debian is not checked anymore.

I've looked here: [https://bugs.launchpad.net/ubuntu/+bug/66705]("https://bugs.launchpad.net/ubuntu/+bug/66705")
but it seems my username already IS the owner for .config and .local
I've looked here: [http://ubuntuforums.org/showthread.php?t=460536&highlight=alacarte]("http://ubuntuforums.org/showthread.php?t=460536&highlight=alacarte")
but the responses he gets does not help me (eg: i'm trying to add an item not remove one so simply deleting a line from a file won't work and that 'automatically save changes to session' did not seem to affect anything at all)

Adding another panel and attempting to check Debian on that one results in the same problem.

Note: i can uncheck/check items that are already checked and changes take place. however, if an item is not checked (eg: accessibility menu) and i try to check it, it will actually UNCHECK it within a few seconds or the next time i goto edit menus. i've done this through terminal > sudo alacarte, right-click edit menus, and System Preferences Main Menu all with the exact same result. I also get no error messages from using the terminal -> sudo alacarte (not sure if you would or not but i think it was asked in another post)

I've reinstalled alacarte from the synaptic package manager. The result is the same problem.

---

### Post by Doctoxic on 2007-06-12
i have exactly the same problem - though i used Automatix to try and install the Debian Menu  - its not there and won't stay ticked

any ideas how to fix this - i am thinking maybe its to do with 'permissions' but wouldn't know where to look


many thanks

Doc

---

### Post by mcduck on 2007-06-12
have you actually installed the Debian Menu? I think the package is called 'menu', and after installing it you also need to run some command to populate the Debian Menu. When that's done, you should be able to use the menu editor to enable the menu in side Applications (if installing & configuring the debian menu doesn't do that for you)

---

### Post by Doctoxic on 2007-06-12
thanks mcduck

i had installed it through automatix, but it wasn't displaying - though it was in the menu selction proggy but you just couldn't select it (well you could 'tick it' but it lost the ticj as you exited

i have since uninstalled menu through automatix and reinstalled through synaptic - but no change

i ran 'update-menus' but this didn't have any effect either


this is all very odd as i had the menu in my previous install

any help to fix this much appreciated

thanks

Diss

---

### Post by Doctoxic on 2007-06-12
i think i found the prob - though don’t know how to fix it

i did sudo alacarte and there is the debian menu as an option and all ‘ticked’

it seems to be some sort of permission problem - any idea how i can fix this?

thanks

---

