---
title: "Ubuntu Edgy: Installing A Network Printer"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by RKCole on 2006-12-05
Hello, everyone.

As part of the final project for my Linux class, I have to install/use a network printer in our Linux lab at the college.  There are many other things which I must do as well (such as setting up FTP/SSH/Samba servers), but that will not be too difficult (although I am unsure of how to create a Samba share, but I'll save that for another post if need be).

My problem is that I am unaware of how to add a network printer in Ubuntu Edgy.  Everyone else in the class decided to use Fedora Core for their final projects (as we had to install a distribution of our choice)...The obvious choice for me was Ubuntu as, in my opinion, Ubuntu has the best accessibility by far for blind users.

I am unsure of the type of printer, but I am positive that it is one which Linux is compatible with (or else it would not be in the Linux lab :) ).  I don't know if this is the correct way to add a network printer, but I tried 

System->Administration->Printing->New Printer

but ti was to no avail.  The cups.add screen (which I believe is what displays to show that the system is searching for a printer) did nothing for at least ten minutes.

So, in short, what is the best way of adding a network (classroom) printer in Ubuntu Edgy?  I'm stumped. (haha)

I would greatly appreciate any help/input.

Thanks, everyone.

---

### Post by Tilex on 2006-12-05
I am not sure about Ubuntu, but I know that under Kubuntu, it is rather easy.  In your System Preferences->Printer, you click on the Print Server tab (which is a top-down menu) and click on 'Configure Server'.  Then there is the Wizard showing up that is just waiting for your professional input! ;)

---

### Post by RMorris78 on 2006-12-05
If Samba is configured correctly (i know you said you dont have a share), try going to 

[http://localhost:631](http://localhost:631)

That should get you to the CUPS web interface.  I found it self explainitory from there.

Heres some Samba info if you need to set it up
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba)

And this is how to do it in Xubuntu, but i would assume its the same
[http://howto.gumph.org/content/use-smb-printer-in-xubuntu/](http://howto.gumph.org/content/use-smb-printer-in-xubuntu/)

---

