---
title: "How can I get Microsoft Publisher working in Ubuntu?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by szaemon on 2007-06-27
How can I get Microsoft Publisher working in Ubuntu? Or is there a good program that I can use to replace it which can handle .pub files?

---

### Post by BHelts on 2007-06-27
[This Link]("http://appdb.winehq.org/appview.php?iAppId=663") states that no other apps have been found to handle .pub files for linux.  I don't know how well Publisher will work in wine though.

---

### Post by szaemon on 2007-06-27
Discouraging, but thank you.

Does anyone know how well MS Publisher works under wine? Is the best or the only thing that  let you run MS programs.?

---

### Post by oilchangeguy on 2007-06-27
> **szaemon said:**
> How can I get Microsoft Publisher working in Ubuntu? Or is there a good program that I can use to replace it which can handle .pub files?


if open office won't work for you, try a non free program called cross over office. see [www.codeweavers.com](www.codeweavers.com)

---

### Post by ramjet_1953 on 2007-06-27
You could also have a look at [COLOR="Blue"]Scribus[/COLOR], which is a Linux DTP package.

It can be installed using [COLOR="Blue"]Applications>Add/Remove[/COLOR]. It is in the [COLOR="Blue"]Graphics[/COLOR] section.

Here is a link to the home page:

[http://www.scribus.net/](http://www.scribus.net/)

Regards,
Roger :cool:

---

### Post by szaemon on 2007-06-29
> **oilchangeguy said:**
> if open office won't work for you,..[www.codeweavers.com](www.codeweavers.com)

Is that to say open office should or even could be made to open.pub files without damaging them?

---

### Post by mlentink on 2007-06-29
> **szaemon said:**
> Is that to say open office should or even could be made to open.pub files without damaging them?
No. Is there a particular reason why you want to use these .pub files? Most printers go for .indd (Adobe Indesign) or pdf.  Scribus will do the latter very well.

---

### Post by hyper_ch on 2007-06-29
or you could install vmware or vbox to run a virtual windows within your computer....

That way you can run publisher easily... however the speed/usability depends on your hardware...

---

### Post by scheuri on 2007-06-29
To summarise...:

1) No, you are not able to run Microsoft Publisher in Linux just like this (without the use of some sort of virtualisation or emulation).
2) No, as far as I know there is NO program being able to open .pub-files (execpt Publisher itself, of course).

You may try following steps:

1) Use virtualbox, vmware or other kind of virtualisation program to run Microsoft Windows (XP or whatever). Within the virtualised Windows you can run Publisher.
It was already pointed out that performance may suffer.
2) Try to run Publisher with an emulation programm such as wine, cedega or crossover. With those "tools" you might be able to install and run publisher without the need of windows. However, it may just not work.
3) You look for another tool which does the same you need but runs under linux (and maybe even windows, too).

Greetings
scheuri

---

### Post by sawjew on 2007-06-29
I have installed Publisher 2002 using Crossover Office and then saved any I wanted to keep as PDF files using CupsPDF.  Publisher is not a particularly good desktop publishing program and it is very limited because no other software supports its format.  I think Scribus is probably about the best open source alternative but it has a very limited selection of templates.  You can install the extra templates package but it still has nothing on Publisher's template range.

If you want to just convert your files to PDF you could download the trial version of Crossover Office and install Publisher, then install CupsPDF and print the files to PDF.  If you want to do any editing after you have converted them to PDF you can install PDFedit (from here [http://www.getdeb.net/]("http://www.getdeb.net/")) which can do a reasonable amount of editing of PDF files.

Good luck and have fun.

---

### Post by szaemon on 2007-06-29
> **mlentink said:**
> Is there a particular reason why you want to use these .pub files? 
Yes. A very particular reason. I have been using Publisher for a quite a while and much of my work is stored as .pub. I can't discard it nor can I afford to have any of it take on a new look. I need it to remain exactly the same. Which brings to mind another query I have. How can I bring in the Fonts and Artwork from MS Word and MS Publisher??

---

### Post by szaemon on 2007-06-29
> **scheuri said:**
> 
1) Use virtualbox, vmware or other kind of virtualisation program to run Microsoft Windows 
2) Try to run Publisher with an emulation programm such as wine, cedega or crossover.
3) You look for another tool 

Well, Thank you all for your help a Newb couldn't ask for better guidance. I think I'll choose option #1 and work my way down, Using another program like (scribe for instance) seems the least likely method of preserving the files in tact.  

So, any thoughts on which virtualization program I should choose?

---

### Post by AndyCooll on 2007-06-29
Which virtualization program you use is entirely your own choice. You can successfully create an XP image in Virtualbox, Qemu or VMware, and all work fine.

VMware is the most established, but is only free "as in beer", VirtualBox and Qemu are open-source. You can install all of them from the repos I believe, though for VMware you'll need the server edition to create your image. If you do a search there are quite a few howtos on how to create Windows images.

Pays your money takes your pick so to speak. 

:cool:

---

### Post by mlentink on 2007-06-29
> **szaemon said:**
> So, any thoughts on which virtualization program I should choose?

I have no advice to give, but eh, do you still have a Windows license? If not, going the VM-route will set you back a bundle. If you don't want that, I'd give Crossover a try first. SInce most of the Office stuff works, there's a pretty good chance that Publisher (which in my personal opinion s**** as a DTP-tool) will run as well.

I'll have a look at their site or at the winhq site.

---

### Post by mlentink on 2007-06-29
Codeweavers (Crossover) say [this]("http://www.codeweavers.com/compatibility/browse/company/?cw=c0b564b32b4f6ff29472433689987557;company_id=1;sort%5Bapp_name%5D=ASC;curPos=100"), and WineHQ says nothing about Publisher, which is not good news.
I hope you still have that Mickeysoft license....

---

### Post by sawjew on 2007-06-29
As I mentioned in a previous post, I have Publisher 2002 (XP) working using Crossover Office version 6.10 (the latest version).  I just selected to install Microsoft Office XP in the Crossover install menu and it seems to be working without any hitches.  I looked at the Crossover compatibility site and I have had none of the issues mentioned on the site.  I would download the demo version of Crossover and try it.  It is very easy to use and if it works the license is only about $35US I think.  If you want to run any other Windows apps it could come in handy as well and it is much easier and runs faster than Windows in vmware.  (I do have Windows in Vmware for the odd app but the only thing I have used it for so far is to recover some old Msbackup files).

My advice is try to go away from Publisher but if you can't try Crossover first.  By the way if you just want to save the documents than converting them to PDF will preserve all your formatting and anyone can open and read them.

PS: I have attached a screenshot of Publisher working in Ubuntu via Crossover Office

---

### Post by mlentink on 2007-06-29
> **sawjew said:**
> My advice is try to go away from Publisher but if you can't try Crossover first.  By the way if you just want to save the documents than converting them to PDF will preserve all your formatting and anyone can open and read them.

I second that. 
Good advice. mate!

---

### Post by szaemon on 2007-07-01
> **sawjew said:**
> By the way if you just want to save the documents than converting them to PDF will preserve all your formatting and anyone can open and read them.

> **mlentink said:**
> 
I hope you still have that Mickeysoft license....

Thanks for all the advice. The files are not for opening and reading, they are textbooks which need to maintain form as more and more are added to the series. Perhaps I will have to keep Windows and MS Publisher running on a separate partition. I haven't dumped Windows yet, it just isn't in use as my main OS.

---

### Post by jonom on 2007-07-01
> **szaemon said:**
> Perhaps I will have to keep Windows and MS Publisher running on a separate partition.
Use a virtual machine instead (as suggest further up). Virtualbox is quite easy to use. All you need is a windows install disc and you're good to go (oh, and you're MS Office install discs of course)! Having a decent amount of RAM in your computer helps a lot. ;)

You can set up a shared folder on your drive for sharing files between ubuntu and the windows virtual machine.

---

### Post by whistlerspa on 2007-07-01
or you could install Wine.

besure topen the virtual drive before installing pub from its cd

---

### Post by Sand Lee on 2007-07-28
I use this website to view publisher files. It converts them into PDF files which have the website address on the sides -- nothing unbearable really.
[http://www.k2pdf.com/convert.html](http://www.k2pdf.com/convert.html)

---

### Post by fistfullofroses on 2007-07-28
M$ .pub can only be opened via M$ programs. If you truly need to use M$ .pub files I think you only have three options.

1. k2pdf.com/convert.html will convert .pub files into pdf files which can then be opened by open office publisher. 

2. You could use an emulation program to virtualize windows and run publisher through the VM

3. You can dual boot and have windows on one partition, linux on another.

---

### Post by Mornedhel on 2007-07-28
God, 4 exact identical threads made the front page. (And Sand Lee copy-pasted his - relevant - answer across the three of them.) Sometimes I wonder if the Search function shouldn't be a mandatory step before new threads are posted ?...

---

### Post by freesitebuilder on 2007-07-28
I know nothing will open publisher files except publisher - I'm trying Scribus, which is a bit more than I need, and Viva Designer, which is more like publisher.  Viva is here: [http://software.viva.de/english/](http://software.viva.de/english/) (I don't think it's in the repositories). There's a beginners guide  also [http://software.viva.de/english/service/download-english/](http://software.viva.de/english/service/download-english/)

---

### Post by Sand Lee on 2007-07-29
Oops! sorry about that, I didn't know that would be an affect. :lolflag: I just wanted help.

---

