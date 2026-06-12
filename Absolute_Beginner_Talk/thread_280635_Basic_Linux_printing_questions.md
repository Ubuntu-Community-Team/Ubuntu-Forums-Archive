---
title: "Basic Linux printing questions"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by steve.horsley on 2006-10-19
I have noticed that the print dialogs from my applications don't offer printer settings like print quality. I have set up 3 printers in the gnome printer admin thingy, all pointing to the same physical printer but each with a different print quality and a matching name - draft, normal and best. Now at least, I can select a printer to match from the application. 

I sort of expected a print dialog from the application to offer the available print qualities, like Windows does. Is this the normal way printing is done in Linux, or am I missing a trick? 


Secondly, I can also presumably edit configurations from [http://localhost:631/printers](http://localhost:631/printers). Is there a possible conflict between these two? This may be a moot question as I don't seem to know a username and password for the cups web page.

---

### Post by mssever on 2006-10-19
Gnome doesn't seem to have standardized the print dialog yet. In OpenOffice, you can click on properties > device tab > printout mode. In Firefox, there are no options, and in evince, print quality isn't one of the options.

As far as using the web interface goes, it's perfectly safe--but I don't know what would happen if you tried to use both at the same time. For some crazy reason, cups (the printing system) doesn't use the same password as everything else on the system. [This post]("http://ubuntuforums.org/showpost.php?p=1463873&postcount=11") enabled me to use the web interface.

---

### Post by steve.horsley on 2006-10-20
Gosh yes! I hadn't noticed that tab. So it looks as though Gnome **can** let the pronter options through, it's just that the applications need to catch up. I guess that's a matter of time.

Thanks for the link on the web interface. I'll bookmark that and give it a try.

---

### Post by ReaderRat on 2006-10-20
I don't have a Device tab in Properties...    Where did you find it?.....ReaderRat

---

### Post by steve.horsley on 2006-10-20
> **ReaderRat said:**
> I don't have a Device tab in Properties...    Where did you find it?.....ReaderRat

It's OOo v2.0.2 - the one in the Ubuntu distros. I suppose it's possible that the Ubuntu/Debina guys have added that dialog and that the standard download from OOo doesn't have it - I haven't checked that.

File->Print...->Properties 
or 
File->Printer Settings->Properties

See attached piccy.

---

