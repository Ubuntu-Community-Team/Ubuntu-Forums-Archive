---
title: "The GIMP"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by tray02 on 2005-09-18
I'm having problems with printing stuff from The GIMP....I think I need the printing plug-in ...or something like that....(it says that on the first paper that comes out)...I also need to know how to get the help files for the GIMP ...and I guess anything else that would make The GIMP fully functional....

thank you for your help

---

### Post by wvslkr on 2005-09-18
Open Synaptic and do a search gimp.  It will bring up a list of all the gimp things in the repositories.  I think you will be able to find what you need.  Make sure you have all your repositories enabled.  If you don't know how check the unofficial users guide.  

If you need more info ask away.

Hope that helps.

---

### Post by tray02 on 2005-09-18
synaptic?...where's that?

nevermind....i found it....

but it says that the CUPS package is already installed for GIMP...

---

### Post by wvslkr on 2005-09-18
System>Administration>Synaptic package manager If you have it installed.  If not open a terminal and type>sudo apt-get install synaptic.

---

### Post by tray02 on 2005-09-18
okay...it think I installed as many gimp files as there are....(not really sure)...but now NOTHING prints....(no blank papers or anything comes out...)

---

### Post by tray02 on 2005-09-18
this stupid printer won't print any gimp files...it just keeps printing out blank pages (other than the first page which says...

%!PS-Adobe_3.0
                         %%Creator: Print plug-in V4.2 for GIMP/Gimp-Print 4.2.7 (15 Jul 20


.....near the top of the page....)

thank you for your help

---

### Post by xmastree on 2005-09-18
Just a thought...
If you really need to print something, you can always save the file in some standard format, then create a document in open office and insert the image. Then print that.

It doesn't fix your problem, but it might get the job done.

---

### Post by tray02 on 2005-09-18
any ideas on how to fix it though....:confused:

---

### Post by TristanMike on 2005-09-18
What do you have as your "Printer Model"? And what happens if you "Print to File"?

---

### Post by tray02 on 2005-09-18
now i feel stupid.....it wouldn't print because it was in xcf format....when I changed it to jpeg...it worked (but I printed it using another program..) ](*,)

---

### Post by jeremy on 2005-09-21
You have to set up your printer within Gimp.
Open a file in Gimp, then got to File -> Print... and in the dialogue that opens, under 'Printer Settings' go to 'Setup printer'  and choose your printer.,

---

