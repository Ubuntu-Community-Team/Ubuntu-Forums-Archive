---
title: "Can't open GIMP Help file nor access the Online documentation"
date: 2011-10-20
forum: Art &amp; Design
---

### Post by PayPaul on 2011-10-20
Has anyone else had trouble accessing the help files from GIMP or getting to the English version of the GIMP documentation? It's been going on for some time now. Is there something wrong with the site itself?

This is the message I got when pressing F1

*Could not open 'http://docs.gimp.org/2.6/en/gimp-help.xml' for reading: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.*

My internet connection is working. I don't know if there are security measures in place from GIMP but I think it's the site that's the problem. I'm just not sure.

I just checked the Website home page. Heres' what has been said.

[I]Due to relocation onto a different server, the following services are currently not available:  
[/I] 
[LIST]
[*]*Mailing lists (lists.xcf.berkeley.edu)*
[*]*FTP Downloads (ftp.gimp.org)*
[*]*Documentation (docs.gimp.org)*
[*]*Developer website (developer.gimp.org)*
[*]*Developer Wiki (wiki.gimp.org)*
[/LIST]
I'm surprised there hasn't been a thread about this. Is there any other way to get this documentation? The administrators of the GIMP say nothing further. They speak of the FTP and Developers sites being back up but I can't find anything through the links posted that contains the documentation.

---

### Post by robert shearer on 2011-10-20
Have you downloaded and installed the help file...?

```
sudo apt-get install gimp-help-en
``` 

Restart gimp, then  F1

---

### Post by PayPaul on 2011-10-21
> **robert shearer said:**
> Have you downloaded and installed the help file...?

```
sudo apt-get install gimp-help-en
```Restart gimp, then  F1

A great idea. However the Help files still come off the website which hasn't updated the status of those files. I received the same error message as before after restarting GIMP and clicking on Help. This apt-get command went through all the normal paces but failed to load an actual help file to my machine. Apparently the help feature in GIMP relies solely upon the GIMP Website.

Thank you for the tip but it's in the GIMPs corner now. I wonder if any members of that community would come on to this thread to weigh in on this problem.

---

### Post by Rodney9 on 2011-10-21
Try going into Synaptic and check that gimp help is installed correctly, I installed through synaptic and it brings up it's own help, see below

---

### Post by PayPaul on 2011-10-21
> **Rodney9 said:**
> Try going into Synaptic and check that gimp help is installed correctly, I installed through synaptic and it brings up it's own help, see below
A good suggestion and thank you. Searching for Gimp Help produced the indication that Gimp-help-en is installed. However there's a caveat which goes back to my original problem. Here is how the Gimp Help is described in the Synaptic Manager.

[COLOR=SeaGreen][I]This package contains the documentation files for the GIMP designed for use
with the internal GIMP help browser or external web browsers.

This package contains the documentation for the GIMP in English.[/I][/COLOR]

The key phrase here is "[COLOR=Red]**or **[/COLOR]external web browsers". Installation of Gimp-Help-En does not guarantee that the document will be internally installed. In my case, it isn't. How many others here have found that Help is no longer available because the Gimp website documentation is no longer available?

---

### Post by Rodney9 on 2011-10-21
Did you also install gimp-help-common ?

The website help is still on-line - [http://docs.gimp.org/2.6/en/](http://docs.gimp.org/2.6/en/)

Plus there are an amazing amount of other help/tutorials on-line - [http://goo.gl/Tj0M6](http://goo.gl/Tj0M6)

---

### Post by PayPaul on 2011-10-21
Thanks for that link. I'll bookmark it and hope it stays put. From the main site I was unable to access it. 

I'll also try the help-common with an apt-get command.

---

### Post by robert shearer on 2011-10-22
So you're pulling my chain...?

```
sudo apt-get install gimp-help-en
```

when run in a terminal pulls in gimp-help-common as a dependency and if you accept then installs **both**.

These come from the **Ubuntu repos** and have nothing to do with the gimp website and if it is up or not !!

I have just run the code on a new install of Oneric and restarted Gimp then F1 and got the search-able local help file.

> This package contains the documentation files for the GIMP designed for use
with the **internal GIMP help browser** or external web browsers.
 Thats what F1 does..

> The key phrase here is "or external web browsers". Installation of Gimp-Help-En does not guarantee that the document will be internally installed. In my case, it isn't. How many others here have found that Help is no longer available because the Gimp website documentation is no longer available?

> "or external web browsers" simply means that you can navigate to the locally installed help documents, right click and choose to open with your browser eg Firefox and read them **off-line**. Most people just hit F1 and have the Gimp help browser automatically read the local package.

Don't know what you're doing . 
Are you following the advice here ....?

---

### Post by PayPaul on 2011-10-22
Nobody is pulling your chain. Did the very thing you suggested in Terminal, accepted all the requests made during the install process and exited terminal after it was complete. Then I opened up GIMP, pressed F1 and got that message posted above. How can I navigate to the locally installed Help documents. Should I only have to access them from GIMP? It's ridiculous I should have to do anything else. The link to the document site will do for now.

---

### Post by prokoudine on 2011-10-22
> **PayPaul said:**
> Nobody is pulling your chain. Did the very thing you suggested in Terminal, accepted all the requests made during the install process and exited terminal after it was complete. Then I opened up GIMP, pressed F1 and got that message posted above. How can I navigate to the locally installed Help documents. Should I only have to access them from GIMP? It's ridiculous I should have to do anything else. The link to the document site will do for now.

Could you please summarize the issue you are having? I fail to see what is wrong. The internal browser works, docs.gimp.org is back online. What else needs fixing?

---

### Post by ofnuts on 2011-10-22
> **prokoudine said:**
> Could you please summarize the issue you are having? I fail to see what is wrong. The internal browser works, docs.gimp.org is back online. What else needs fixing?
Yes, docs.gimp.org is back online, but that's a recent miracle :)

If he installed the local hep, the OP may also want to check that Gimp has been properly notified in "Edit/Prefrences/Help system"

---

### Post by PayPaul on 2011-10-22
> **prokoudine said:**
> Could you please summarize the issue you are having? I fail to see what is wrong. The internal browser works, docs.gimp.org is back online. What else needs fixing?

Apparently NOW the Gimp docs are back online. They weren't a few days ago when I posted this. I'm glad to see that's the case. The Gimp Help command now works as well from the program. Hooray!!

                                      :-({|=:-({|=:-({|=:-({|=:-({|=:-({|=

---

### Post by prokoudine on 2011-10-22
> **PayPaul said:**
> Apparently NOW the Gimp docs are back online. They weren't a few days ago when I posted this. I'm glad to see that's the case. The Gimp Help command now works as well from the program. Hooray!!

Ah, so this is solved. Great :)

---

