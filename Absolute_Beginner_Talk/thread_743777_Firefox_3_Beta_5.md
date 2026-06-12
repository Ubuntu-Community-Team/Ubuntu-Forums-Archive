---
title: "Firefox 3 Beta 5"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Cephaus on 2008-04-02
Im totally confused on how im supposed to install it

anyone help please

---

### Post by Xiong Chiamiov on 2008-04-02
Is there any particular reason why you need the beta?

---

### Post by Sef on 2008-04-02
> Im totally confused on how im supposed to install it

Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by jordanmthomas on 2008-04-02
All you need to do is download it from their site and extract somewhere.
Then, run firefox from within the extracted directories.
I like to put things like this in /opt.

On a related note, I'm currently compiling the new beta.  b4 didn't compile for me, so I am hoping this one will.

---

### Post by marine63 on 2008-04-03
extract the folder from the tar .gz 
in terminal type
gksudo nautilus
and then your password
in /usr/lib
drag and drop the folder (from the tar .gz) but before you do this rename the folder from "firefox" to "firefox3b5" or w/e
uninstall firefox 3b4 in synaptic manager


or you can wait till ubuntu catch up and install firefox 3.0 beta in repostiory or update

---

### Post by The Titan on 2008-04-03
> **jordanmthomas said:**
> All you need to do is download it from their site and extract somewhere.
Then, run firefox from within the extracted directories.
I like to put things like this in /opt.

On a related note, I'm currently compiling the new beta.  b4 didn't compile for me, so I am hoping this one will.
thats what i did, works fine.  And i can still have version 2 even though i don't use it.  The beta is pretty stable if you ask me.

---

### Post by jordanmthomas on 2008-04-03
> **marine63 said:**
> 
or you can wait till ubuntu catch up and install firefox 3.0 beta in repostiory or update

This won't happen until Hardy comes out.  Why they'd release a beta into an LTS I don't know, but they supposedly are.

---

### Post by Cephaus on 2008-04-03
Got it to work, but flash wont install for me

---

### Post by marine63 on 2008-04-03
> **jordanmthomas said:**
> This won't happen until Hardy comes out.  Why they'd release a beta into an LTS I don't know, but they supposedly are.

shrug i got my beta 5 working so it doesnt matter much to me :)

> **Cephaus said:**
> Got it to work, but flash wont install for me
:( srry to hear that can you be more specific?

---

### Post by The Titan on 2008-04-03
> **Cephaus said:**
> Got it to work, but flash wont install for me
for some reason i can never get flash to install right on the first try in firefox ever.  Go to synaptic and uninstall it then download it from the site and install it with the bin file.  Thats wha i always have to do.

edit: (you posted at the same time)
> 
shrug i got my beta 5 working so it doesnt matter much to me :smile:

lol at that, same here

---

### Post by Cephaus on 2008-04-03
> **marine63 said:**
> shrug i got my beta 5 working so it doesnt matter much to me :)


:( srry to hear that can you be more specific?

It says

"Firefox could not install this item because "install-9wr..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem."

---

### Post by The Titan on 2008-04-03
> **Cephaus said:**
> It says

"Firefox could not install this item because "install-9wr..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem."
Download your file from [here]("http://www.mozilla.com/en-US/firefox/all-beta.html").  Extract that somewhere. 

then in the terminal
```

cd /wherever/you/extracted/it
./firefox

```
thats it, you will be looking at ff 3.0b5.  then you can create a launcher for it.  I'm sure you can figure that out.

---

### Post by Cephaus on 2008-04-03
> **The Titan said:**
> Download your file from [here]("http://www.mozilla.com/en-US/firefox/all-beta.html").  Extract that somewhere. 

then in the terminal
```

cd /wherever/you/extracted/it
./firefox

```
thats it, you will be looking at ff 3.0b5.  then you can create a launcher for it.  I'm sure you can figure that out.

No, I got FF3B5 to work 

Its flash that says the error

---

### Post by The Titan on 2008-04-03
> **Cephaus said:**
> No, I got FF3B5 to work 

Its flash that says the error
oh my bad =/.  Have you tried downloading the massive archive for developers?  it has different revisions in there and rev 48 worked best for me.  I can't find the archive but its on there site and its hidden well (unintentionally i think) it's too big to attach so heres a link to my server wher eit will be in like 30 seconds.  [http://test.titanstechnologies.net/flash](http://test.titanstechnologies.net/flash)

---

### Post by darkone99 on 2008-04-03
> **jordanmthomas said:**
> All you need to do is download it from their site and extract somewhere.
Then, run firefox from within the extracted directories.
I like to put things like this in /opt.

On a related note, I'm currently compiling the new beta.  b4 didn't compile for me, so I am hoping this one will.

I tried this but failed . i dont have a /opt on my system .
and how do you run firefox from the extracted directory

---

### Post by philinux on 2008-04-03
/opt is a directory in the file system, not in your home directory.

You need 

gksudo nautilus to access it and copy files to.

---

### Post by Cephaus on 2008-04-03
> **The Titan said:**
> oh my bad =/.  Have you tried downloading the massive archive for developers?  it has different revisions in there and rev 48 worked best for me.  I can't find the archive but its on there site and its hidden well (unintentionally i think) it's too big to attach so heres a link to my server wher eit will be in like 30 seconds.  [http://test.titanstechnologies.net/flash](http://test.titanstechnologies.net/flash)


How do I install it?

---

### Post by Cephaus on 2008-04-03
Help please

---

### Post by privaterolf on 2008-04-03
I bet you've tried this, but...

Have you tried using Adobe's Official Flash plug-in, compiled from Source?

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

They should have directions there.

Select the .tar.gz package.

---

### Post by The Titan on 2008-04-03
> **Cephaus said:**
> How do I install it?
just extract it and run the bin file

---

### Post by Cephaus on 2008-04-04
> **The Titan said:**
> just extract it and run the bin file

YAY!

It works!

Thank you so much dude! :):-D

---

### Post by The Titan on 2008-04-04
No Problem :) I had much trouble with that and flash is necessary for me so i understand

---

### Post by misfitpierce on 2008-04-12
For flash simply gksu nautilus and hit /usr/lib/non-free-flashplugin and copy the libflash.so into the firefox folder from .tar.gz in plugins and run from out of folder and flash will work. Enjoy.

---

