---
title: "Feisty Fawn's Migration Assistant ..."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by ageer1 on 2007-04-23
doesnt seem to exist if you use the alternate Installation CD. Does anyone know of a way to install or otherwise use it post alternate installation (I'm using a bootloader,so had to use the alternate) or will I have to transfer everything from IE favorites to address books manually.

Thanks for any (Hopefully positive) input.
Joe

---

### Post by Jeroensum on 2007-04-24
If you already have another OS('s)  installed Ubuntu will most probably find them and list them in GRUB after the installation. During or better said, during the installation Ubuntu will show you which OS's have been found. If you're not happy with it, just reboot and all will be fine.

Otherwise you could try to apt-get ubiquity (the ubuntu live isntaller) and after apt-getting it, run sudo updatedb and try if you can locate ma-ask and ma-apply and such. Those are the tools that controll the profile-move process. 

Hope this gets you on your way.

---

### Post by ageer1 on 2007-04-24
Thanks for the response, but a little over my head. I've been a Linux & Ubuntu user for about 24 hours now. 

So far I am loving it :) but sure would like to be able to transfer my 10 plus years of contacts, address books etc to it. :confused: 

I decided to set it up on a bootloader to be able to try several flavors of Linux before deciding on one, but after playing with it and getting my network printer and scanner working with no sweat, I'm considering abandoning that approach and just keeping Ubuntu! 

Would it be possible to run the Live CD/Install disk to be able to use the migration manager without changing my installation to date?

Or any other thoughts?

Joe

---

### Post by Jeroensum on 2007-04-25
Well, you could keep your current setup and do the migration manually:

-You can mount your windows parition(s) in Linux (if Ubuntu hasn' t done this allready). And access all needed files :-)

-If you were using Outlook (not outlook express), you can apt-get readpst to convert your pst file(s) to mbox format (allmost every linux mail program can read such a file). This tool will also convert your contacts to .vcf (vcard format) which can be imported into linux mail programs.
PST files are usually stored in:
C:/Documents and Settings/<user profile>/Local Settings/Application Data/Microsoft/Outlook/

-Your Internet Explorer Bookmarks can be imported with a plugin or a tool into Firefox checkout this page:
[https://addons.mozilla.org/en-US/firefox/search?q=import+bookmarks&status=4](https://addons.mozilla.org/en-US/firefox/search?q=import+bookmarks&status=4)

I can' t think of any other settings that should be imported but if you have more and this solution fits you then let me know :)

---

### Post by ageer1 on 2007-04-26
Thanks for the reply but readpst get me an  "Invalid operation readpst" error, Same with sudo! Couldn't figure out how to use the plug in. Remember I don't even know how to run a shell script yet!

Thanks for trying,
Joe

---

### Post by Julian Lewis on 2007-06-15
> **Jeroensum said:**
> Well, you could keep your current setup and do the migration manually:

-You can mount your windows parition(s) in Linux (if Ubuntu hasn' t done this allready). And access all needed files :-)

-If you were using Outlook (not outlook express), you can apt-get readpst to convert your pst file(s) to mbox format (allmost every linux mail program can read such a file). This tool will also convert your contacts to .vcf (vcard format) which can be imported into linux mail programs.
PST files are usually stored in:
C:/Documents and Settings/<user profile>/Local Settings/Application Data/Microsoft/Outlook/

-Your Internet Explorer Bookmarks can be imported with a plugin or a tool into Firefox checkout this page:
[https://addons.mozilla.org/en-US/firefox/search?q=import+bookmarks&status=4](https://addons.mozilla.org/en-US/firefox/search?q=import+bookmarks&status=4)

I can' t think of any other settings that should be imported but if you have more and this solution fits you then let me know :)
Just as I thought I was getting somewhere, readpst gives me this ....

lewis@JuliansLaptop:~/Desktop/pst$ readpst backup.pst
Opening PST file and indexes...
debug_fp is NULL
unknown index structure. Could this be a new Outlook 2003 PST file?
debug_fp is NULL
Error opening File

Is there a version of readpst that works with 2003 outloock, or am I condemmed to use outlook, there is no way to export my 6000 odd email addresses.

This is what I tried so far ...
export as a CSV and import it. I end up with a garbage address book.

Install thunderbird on the windows system ,import export bla bla. Thunderbird just Jams up and I have to kill it off with task manager.

Take pst file to my homw windows system, import the CFV, install thunderbird bla bla. This wont work because I have only got office 2000 at home and it can't understand 2003 pst files.

So it looks like there is NO WAY to import an outlook 2003 address book into either evolution or thunderbird in my case. My work PC is not managed by me, and thats where I want my address book from.

---

### Post by Julian Lewis on 2007-06-15
Can anyone understand this ?

---

### Post by forestpixie on 2007-06-16
saw this thread today and remembered reading yours yesterday perhaps it'll help?

[http://ubuntuforums.org/showthread.php?t=475182](http://ubuntuforums.org/showthread.php?t=475182) 

If so it'll be thanks to PartisanEntity

:)

---

