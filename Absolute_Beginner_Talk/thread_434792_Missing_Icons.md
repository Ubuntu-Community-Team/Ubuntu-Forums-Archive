---
title: "Missing Icons"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by germund on 2007-05-06
I have been having trouble getting an anti virus program running on my system (Edubunto 7.04).  I installed Aegis Virus Scanner using the Add/Remove Programs utility, but the icon does not show up in the menu.  I know the program is there, I had it up and running once.  I just can't get the icon to appear in the menu.  I have tried installing and uninstalling it 7 or 8 times.  It never shows up.  Onece I tried to place the icon manually, but I couldn't make hide nor hair of the file system in Linux.

---

### Post by Happy_Man on 2007-05-06
Try refreshing the gnome-panel by logging out and then logging back in. It should show up.

---

### Post by lluisanunez on 2007-05-06
I think Aegis is a command line program, try opening a terminal and typing
```
aegis
```
Synaptic also provides 2 user interfaces: TK gui and web gui
But, what do you want aegis for?

---

### Post by germund on 2007-05-06
I want a virus scanner.  I tried ClamAV, but that one wouldn't work.  Those two are my only two options according to the Add/Remove Programs function.

---

### Post by ubromtoo on 2007-05-23
Am having the same problem with Aegis. Have restarted the computer, didn't help.

  Then I opened a Terminal and typed   aegis   and hit "enter" ; the result was 

          bash: aegis : command not found

When I tried  Application> Accessories> Alacarte menu editor , Aegis is there with the

box already checked.

           Any suggestions ?             :guitar:

---

### Post by ubromtoo on 2007-05-23
GERMUND:

        Open a terminal and type      " aegis-virus-scanner "       then hit enter.

this will bring up  Aegis program.


         Also, you can add add Aegis to the "Accessories" dropdown menu by :


   Applications> Accessories > Alacarte menu editor ; once the Alacarte menu editor

opens(it takes several seconds) then double-click on "Accessories", click on "File"
 
and then on "New" and fill out the forms.
             
          This works for Dapper 6.06, anyways

---

### Post by matchstich on 2007-06-21
i am on feisty. installed aegis.  same problem as the op. i can find it  in add/remove.

but it is not in accessories.

and when i go to main menu >accessories
it is not listed there.

so , i clicked on add.  

i have to browse to where the program is located.

that is where i get lost
thanks

---

