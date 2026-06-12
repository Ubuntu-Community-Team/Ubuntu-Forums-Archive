---
title: "HowTo: Acrobat Reader Install In Feisty"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by linux4me on 2007-07-02
As much as I would like to be completely open-source, I have to use Acrobat Reader for PDF's for work. Evince just doesn't have the features I need. When I upgraded from Edgy to Feisty, the upgrade uninstalled Acrobat Reader (acroreader) so I had to search around for a way to install it. I found an easy method by searching through the forums, but didn't find all the info in one place, so I thought I would share it in case it might help someone else.

The package for Acrobat Reader for Feisty is available in the [Medibuntu Repositories]("https://help.ubuntu.com/community/Medibuntu"). The first thing you need to do is add them. Open a Terminal (Applications->Accessories->Terminal). Copy/paste the following command and hit Enter:

> echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list

When prompted for your password, type it in and hit Enter. Next, copy/paste this command and hit Enter:

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Exit the terminal by typing "exit" and hitting Enter.

Open Synaptic Package Manager (System->Administration->Synaptic Package Manager). You may be asked for your password again.

Click the "Search" button and enter "acroread" and then Search.

There are four files listed. You'll need the following if you want to use Acrobat Reader and have Firefox automatically open a tab when you click a link to a PDF:

> 
acroread
acroread-escript
mozilla-acroread


If you want to fill out PDF forms, you'll also need acroread-plugins. 

Click the checkbox for each and choose "mark for installation". Click Apply. When you're done, you should have a working link to Acrobat Reader on your Applications->Office Menu, and PDF links you click on in Firefox will automatically open in a new tab.

---

### Post by greg_g on 2007-07-03
Good howto for those that need it.

It should probably be in the "Tutorials and Tips" section though.

greg

---

### Post by moccachino on 2007-07-03
Awesome guide, I just had a pdf File to fill out and I couldn't do it with the standard pdf viewer ... 

Thanks a Lot

---

### Post by dustrho on 2007-07-19
Great tutorial that worked for me, but how do we make Ubuntu open all PDF files with the Adobe Reader instead of the Evince Viewer.

---

### Post by Majorix on 2007-07-19
Right click the file, then go to properties, open with tab, and from there select Adobe Acrobat.

---

### Post by Corvair on 2007-07-22
Thank you for the great post.
Finely I was able to install acroreader

---

### Post by arnold.pietersen on 2007-07-25
Even though I have installed Adobe Reader successfully, Evince stills opens it.  I have right-clicked on a PDF file and when I select Open With only Evince is listed.

Thanks

Arnold

---

### Post by RomeReactor on 2007-07-25
Hi. Run this command from the terminal (Applications->Accessories->Terminal):
```
locate acroread
```
and post the output here.

---

### Post by Mornedhel on 2007-07-25
In the Properties, Open With section, you can choose to Add... an application to the list, and if acroread still doesn't show, type your own command.

---

### Post by LuisC-SM on 2007-09-09
This should be in the howto and tips section IMHO

Luis

---

### Post by salatmensch on 2007-09-24
greetings,

i've just installed the acrobat reader via the packet-manager. however i am still unable to view pdfs: evince AND the acrobat reader won't open pdfs correctly. evince just crashes and the acrobat reader shows only page numbers. xpdf works fine though.

any ideas?
best regards

salat

---

### Post by RomeReactor on 2007-09-24
Hi. Does this happen with only one PDF file, or multiple files? if it just happens with a specific file, perhaps the download is corrupt.

EDIT: sorry, didn't notice the bit about XPDF.

---

### Post by salatmensch on 2007-09-25
i tried several pdfs from different sources, getting the same result...

---

### Post by hyper_ch on 2007-09-25
> **arnold.pietersen said:**
> Even though I have installed Adobe Reader successfully, Evince stills opens it.  I have right-clicked on a PDF file and when I select Open With only Evince is listed.

Thanks

Arnold

Can you type the name of a program in there that it shall open with? If so, just enter:
```

acroread

```

That should do the job.

---

### Post by Corvair on 2008-02-14
Linux4me

Thank you again for the nice script,

I had lost Acroread when updating to 7.10 and was able to reinstal it.
:lolflag:

---

### Post by PmDematagoda on 2008-02-14
This HowTo is meant for Ubuntu 7.04(Feisty Fawn) not Ubuntu 7.10(Gutsy Gibbon) or greater, because of that do not use it in order to install Acrobat Reader on Ubuntu 7.10+.

---

### Post by dca on 2008-02-14
You can also d/l latest Adobe Reader direct from Adobe website.  When you click the' Get Adobe Reader' icon on main page, it knows you're running *nix.  Do not d/l .RPM which it defaults to, click choose different os link.  From the 'Select Installer' drop-down link, select the .deb version and leave the top drop-down on Linux.  Click 'Continue' button.  Then scoll down and click 'Download Adobe Reader' button.  Then select to d/l to your desktop, not install automatically.  Once on your desktop, right-click the file and allow (top option I think) to install using gDebi installer.  Then you're done.  Latest vers at this time is 8.1.2
 
This method has worked for me for 7.04 & 7.10

---

### Post by Corvair on 2008-02-14
But it also works for 7.10 because I just followed the instructions, downloaded the depency and was able to install acroread. One plus

---

### Post by crjackson on 2008-02-14
I can't find mozilla-acroread using synaptic in 7.10x64.  Do I need this and where can I find it?

---

### Post by PmDematagoda on 2008-02-14
> **Corvair said:**
> But it also works for 7.10 because I just followed the instructions, downloaded the depency and was able to install acroread. One plus

It is a risk because of the difference of dependencies and the core between Ubuntu 7.04 and Ubuntu 7.10, so if you want a safe and reliable install on Ubuntu 7.10 then:-
1) Download Acrobat Reader from the official web site.
or
2) Add the Medibuntu repositories that fit your current release and install it using them.

---

