---
title: "Firefox Downloads-window doesn't let me open files."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Golyadkin on 2007-06-19
I am running Firefox 32 bits version inside Feisty Fawn 64 bits because of the Flash issue.
My problem is that when I download a file, and click the "Open" link or rightclick and "Open containing folder nothing happens. The files do not get opened.
This has worked before though, so it is strange.  It is irritating that I now have to browse to my download directory every time and find the file myself, and then open it.

I am using Firefox 2.0.0.4 with just these extensions: AdblockPlus and Firebug.

---

### Post by ThinkBuntu on 2007-06-19
> **Golyadkin said:**
> I am running Firefox 32 bits version inside Feisty Fawn 64 bits because of the Flash issue.
My problem is that when I download a file, and click the "Open" link or rightclick and "Open containing folder nothing happens. The files do not get opened.
This has worked before though, so it is strange.  It is irritating that I now have to browse to my download directory every time and find the file myself, and then open it.

I am using Firefox 2.0.0.4 with just these extensions: AdblockPlus and Firebug.
What sort of a file are you opening?

---

### Post by Golyadkin on 2007-06-19
It does not matter what kind of file.
I have tried and failed to open .tar.gz, .deb,  .txt, .pdf, .odt, .html and .mp3

---

### Post by notwen on 2007-06-19
While in FireFox Tools--->Options--->Content[TAB]--->File Types Area

I can't verify this is the exact way to access the File Types in FireFox on *nix, as I'm currently at work and using the Windows version.  Possibly try locating this and resetting what applications are associated w/ certain file types.  Just an idea.  Hope it helps. =]

---

### Post by Golyadkin on 2007-06-19
Thank you for your comment notwen. The only two entries in that dialog are for SWF and SWL (both shockwave files). There is no reset function, and no other file types in the list.

I checked it out now on the 64 bit version of Firefox, and that dialog is filled with loads of rules to open files.... that is version Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty).

Do I really have to manually insert all these rules into the 32 bit version again?

---

### Post by notwen on 2007-06-19
I have never used 64 bit myself, someone else may have to tell you whether they had similar issues and how they may have remedied said issues.  I'd try adding one or two and see if they work appropriately after you've assigned an application to a file type, if that works at least you know you have a solution.

---

### Post by Golyadkin on 2007-06-19
The problem is, I can't add any rules to that list.

---

### Post by Golyadkin on 2007-06-19
I just thought of something. The rules in the "Content" section are for the situation when I click on a linked file in a website, not for when I downloaded a file and want to open it. Maybe this is related to how Firefox calls nautilus or something?

---

### Post by Golyadkin on 2007-06-20
*shameless bump*

Anyone?

---

### Post by notwen on 2007-06-20
Perhaps try launching Firefox as root to see if that allows you to manually add file types and their application association?  =\  Wish I could help more.  Good luck.

---

### Post by Golyadkin on 2007-06-20
Nah, that doesn't work. There are simply no buttons to add filetypes. Well, nevermind, I guess this one will remain unsolved :)

Thanks anyway for trying to help notwen, I appreciate it.

---

### Post by brack on 2007-08-01
Having the same problem with the same setup. Have Feisty on amd64 and firefox64 works as it should, opens everything from the download manager context menu, but then I tried firefox32 for the sake of java/flash plugins and now in firefox32 when I click on ANY downloaded file there is nothing happening. I have removed firefox32 and install Swiftfox32 with all the plugins - the same issue as in firefox32.
My assumption is that there is something wrong with system software calls in 32 bit firefox. Maybe it looks for 32 bit nautilus(?!!)
:confused::confused::confused:

EDIT: I have noticed that in properties of downloaded files in Download manager on firefox64 field "To:" starts from "file://" like a proper URL but Swiftfox32 doesnt add this definitive addition this could be a problem, how would I fix it?

EDIT: After update of firefox64 till 2.0.0.6 I\ve got "file://" addition to URL of files but... still cannot open anything

---

### Post by brack on 2007-08-01
Again... all my new downloads in Swiftfox32 (see post above) don't have "file://" 
:confused::confused::confused::confused::confused::confused:

---

### Post by engstrom on 2008-01-17
"Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.11) Gecko/20071127 Firefox/2.0.0.11"

I can't open files from the Dowload tool window either.

---

