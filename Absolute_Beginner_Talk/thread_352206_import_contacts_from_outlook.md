---
title: "import contacts from outlook"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-02-03
Does anybdy know how to import contacts from outlook to evolution.
thanks
koli

---

### Post by danielph on 2007-02-03
I did it a long time back. I think you need to export the contacts to a csv (DOS) and then you can import them into Evo.

---

### Post by Levitation on 2007-03-09
But, .csv files don't seem to be an option for importing into Evolution? I mean, when I tried to import .csv it did not allow it. Any ideas? It did allow .vsf but I could only import one at a time (I have 800 contacts)!
Thanks

---

### Post by danielph on 2007-03-09
This has been asked and answered before. It is always better to search the forum before posting.

[http://ubuntuforums.org/showthread.php?t=91687&highlight=evolution+outlook+import](http://ubuntuforums.org/showthread.php?t=91687&highlight=evolution+outlook+import)
[http://ubuntuforums.org/showthread.php?t=53138&highlight=evolution+outlook+import](http://ubuntuforums.org/showthread.php?t=53138&highlight=evolution+outlook+import)

address book
[http://ubuntuforums.org/showthread.php?t=50451&highlight=evolution+outlook+import](http://ubuntuforums.org/showthread.php?t=50451&highlight=evolution+outlook+import)

Enjoy :)

---

### Post by Levitation on 2007-03-14
!

---

### Post by Levitation on 2007-03-14
Mais Monsieur, J'ai une probleme:

Even after checking the links you provided, I could find no answer to this:

How to import more than one .vcf at a time! The Evolution import menu allows for only one .vcf record at a time (I have 800+). I am importing from a .vcf folder which I placed on the desktop. 

Please remember, Je suis un "noobie."

Merci Beaucoups!

---

### Post by danielph on 2007-03-14
Ah a new french word, un noobie. Is it masculine or feminine, maybe it should be une noobie.

I haven't got evolution installed on this box, I use Thunderbird now as it suits me better.

Anyway, what are you using to export (what application's are your addresses currently held in?) and what formats can you export in. Are things like ldif and CSV available? If so, export as a single file and when you import, import as a single file. Job done.

---

### Post by Levitation on 2007-03-14
Evolution will not import .csv and the only other recognizable format I can put it in is .vcf. The original records were in Palm Desktop (.aba), but, since my PDA died I could not use GPilot to sync. So, I exported them as .vcf; However, as I have pointed out, Evo only allows me to import one .vcf (record) at a time. To do that some 800 times...!

---

### Post by mikesignguy on 2007-03-14
the easiest way to import/export cross platform is to us tab deliminated format (.tab)   

some programs use  differeent extentions but then are  all the same

all the field have a tab sepparaating then ( you can see it in any  text editor)

export  the address book into a .tab format then  you can sharee it with all forms of devices and program .  Devices like phones and programs like data bases 

it is a trial and error ..but  once   it's done  it's done

---

### Post by danielph on 2007-03-15
> **Levitation said:**
> Evolution will not import .csv and the only  other recognizable format I can put it in is .vcf. The original records  were in Palm Desktop (.aba), but, since my PDA died I could not use  GPilot to sync. So, I exported them as .vcf; However, as I have pointed  out, Evo only allows me to import one .vcf (record) at a time. To do  that some 800 times...! 
There was a suggestion on another post you have also posted on to try: 

```
cat *.vcf > contacts.vcf 
```I do not know if this works but I  can explain how to do it: 

I am assuming you have all your vcf's in one folder 

1. Open a terminal (Application > Accessories > Terminal) 
2. Change to the folder containing the vcf's. If you placed them in  */home/*<yourusername>/contacts for example, the command to type would be  (~ can be used instead of your current home folder) 
```
cd ~/contacts
``` or ```
cd  */home/*<yourusername>/contacts
```3. ```
cat *.vcf > contacts.vcf  
```4. Fire up Evo, Contacts > File > Import > Import Single File > Select Filename and directory eg ~/contacts/contact.vcf > Select Filetype Vcard

Let me know if you have problems following the instructions, I'll be happy to go through them with you. As I say, never tried this, but it should put all the vcards in one file and if it is formatted correctly import in evo should work.

---

