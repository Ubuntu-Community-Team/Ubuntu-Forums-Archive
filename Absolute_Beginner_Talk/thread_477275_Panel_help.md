---
title: "Panel help?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-06-18
Hello all thanks for helping me all the time now  1 more help . Can any 1 tell me how to get the deleted panel back again I deleted the upper panel now I want it back ..Same if  I delete the lower panel how to get it back..

Help will be appreciated :):KS 

Peace Ds

---

### Post by Dark Star on 2007-06-18
Some body help plz I need it , pretty urgent ! And if then plz suggets some desk lets site except gdesklets where I can download desklets :) Thanks plz reply It urgent plz :)

---

### Post by fakie_flip on 2007-06-18
You could create a new user on your system. The new user will have all the default panels.

---

### Post by Dark Star on 2007-06-18
Naa without adding user  How to add the deleted panell.. And 1 more thing hw to know the command to open an application like I have gDesklets installed and I want to add it to Startup Manager but I did not know the command and did not knew where it is located.. Can u help.. .and plz suggest some widget site from where I can download widget :)

Regards

---

### Post by bigken on 2007-06-18
right click on the exisiting panel select new panel

---

### Post by mcduck on 2007-06-18
Just right-click in any empty space in the panel you still have, select 'Add New Panel' and drag the new panel to to where you want it. Then right-click on the new panel, select 'Add to Panel' and drag&drop the applets you want into the new panel.

I don't remember what applets the top panel has in the default configuration, but at least Menu Bar and Clock applets for sure.

Edit: I think Gdesklets are started with simple 'gdesklets'. Anyway, pretty much all executable files for your programs are in /usr/bin so take a look there and most likely you'll find the right one. Also, 'qhich' is a nice tool for finding the executable of a program, just run 'which appname' in a termianl and it will return path to the executable file of that app. For example 'which firefox' returns '/usr/bin/firefox'.

---

### Post by Dark Star on 2007-06-18
> **bigken said:**
> right click on the exisiting panel select new panel
Aha excellent ,me silly didn't try this out thanks anyways... 1 more problem remaining sir .... Can any 1 gimme link to a site where I can download goo desklets for gDesklets :)

---

### Post by bigken on 2007-06-18
try here [http://www.gdesklets.org/?q=desklet/browse](http://www.gdesklets.org/?q=desklet/browse)

---

### Post by Dark Star on 2007-06-18
> **bigken said:**
> try here [http://www.gdesklets.org/?q=desklet/browse](http://www.gdesklets.org/?q=desklet/browse)
Do u know any other than this I had seen all the desklets and downloaded can I find a site for bettter 1 like transparent calender ? and all

And 1 more thing hw to know the command to open an application like I have gDesklets installed and I want to add it to Startup Manager but I did not know the command and did not knew where it is located.

---

### Post by RomeReactor on 2007-06-18
Hi. To restore your top panel, as has been said before, right-click on your remaining panel (the bottom one) and select "New Panel"; then add to it (by right-clicking on the new panel and selecting "Add to Panel..."):

* Quit...
* Clock
* Volume Control
* Notification Area
* Menu Bar

That's the correct order **from right to left**. Also, if you want to leave it *exactly* as it originally was, add icons for:

* Applications-->Internet-->Firefox
* Applications-->Internet-->Evolution Mail
* System-->Help and Support

next to the **menu** by **dragging and dropping** those icons from the menu, so it looks like this:

---

### Post by Dark Star on 2007-06-18
Thanks for detailed info ...And 1 more thing hw to know the command to open an application like I have gDesklets installed and I want to add it to Startup Manager but I did not know the command and did not knew where it is located.

---

### Post by RomeReactor on 2007-06-18
Looks like I was too slow... For starting gdesklets with your system, go to "System-->Preferences-->Sessions", click "New" and fill out the command with **gdesklets start**.

---

### Post by Dark Star on 2007-06-18
Thanks but how can I know the commands :) Can u tell me ? Plz
And can u suggest some desklets site opther than gdesklets home page :) 

Regards

---

### Post by RomeReactor on 2007-06-18
If you want to manually start gdesklets, press **ALT+F2** and enter **gdesklets**. As for adding more desklets from other sites, sorry, I don't know any.

---

### Post by Dark Star on 2007-06-18
> **RomeReactor said:**
> If you want to manually start gdesklets, press **ALT+F2** and enter **gdesklets**. As for adding more desklets from other sites, sorry, I don't know any.
Thnks again btw how can u tell me how can I know the commands  myself ?Can u tell me ? Plz

---

### Post by 3rdalbum on 2007-06-18
If you go into Synaptic Package Manager, right-click on the "gdesklets" package, select "Properties" from the menu, then go across to the Installed Files tab, that will show you all the files that the gdesklets package has installed.

Any files within a directory that has "bin" in its name (for instance, "/usr/bin", "/usr/local/bin", "/usr/sbin") will be executable. When a file is executable and in one of these "bin" directories, you can run it by typing its name into the terminal or some other place where a command is accepted.

So, Gdesklets probably has "/usr/bin/gdesklets" as one of its installed files, so you can just type "gdesklets" to start it.

EDIT: Some installed programs require extra input at the command-line. To find out exactly what "arguments" or "parameters" need to be "passed" to the program on the command-line, you can usually type "man " and then the name of the program. For instance:

```
man gdesklets
```

That's also what is referred to when someone advises you to "read the man pages".

---

### Post by Thomar on 2007-06-21
> **RomeReactor said:**
> Hi. To restore your top panel, as has been said before, right-click on your remaining panel (the bottom one) and select "New Panel"; then add to it (by right-clicking on the new panel and selecting "Add to Panel..."):

* Quit...
* Clock
* Volume Control
* Notification Area
* Menu Bar

That's the correct order **from right to left**. Also, if you want to leave it *exactly* as it originally was, add icons for:

* Applications-->Internet-->Firefox
* Applications-->Internet-->Evolution Mail
* System-->Help and Support

next to the **menu** by **dragging and dropping** those icons from the menu, so it looks like this:

Aha!  I was looking for those defaults.  I was fiddling around with the panel and tried to remove the divider on the left of the notification area.  I didn't know what the notification area did, so I didn't put it back and I was looking all over for my network and minimized jukebox icons.  Thank you very much.

---

