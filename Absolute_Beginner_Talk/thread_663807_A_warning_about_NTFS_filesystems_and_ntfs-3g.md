---
title: "A warning about NTFS filesystems and ntfs-3g"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by fiddledd on 2008-01-10
Not sure where to post this, so for now at least it's here.

I noticed a problem with ntfs-3g while using Ubuntu, at least I assume the problem is with ntfs-3g. If you save, for example, a Web page and it has illegal characters in the saved filename (assumimg you just save the page with the existing title) and save directly to NTFS, or later transfer to NTFS, with Ubuntu, you can't access this file in Windows. You can't even delete it from DOS, you have to go back to Ubuntu and delete or rename it from there.
I thought I'd warn people so they didn't make the same mistake I did. Sorry if this is posted elsewhere (I did a forum search and found no reference to it).

---

### Post by EXCiD3 on 2008-01-10
What types of characters cause this?

You should post a bug with the ntfs-3g developers: [http://www.ntfs-3g.org/support.html#bugreport](http://www.ntfs-3g.org/support.html#bugreport)

---

### Post by ubuntu-freak on 2008-01-10
It's a Windows bug not ntfs-3g. Windows disallows even common symbols in filenames. For example the > symbol.
 
Nathan

---

### Post by szaka on 2008-01-11
Windows can handle all characters but not all Windows applications. It depends on how the developers of a certain Windows application coded it. Unfortunately many ignores interoperability: [http://ntfs-3g.org/support.html#posixfilenames2](http://ntfs-3g.org/support.html#posixfilenames2)

---

### Post by ubuntu-freak on 2008-01-11
> **szaka said:**
> Windows can handle all characters but not all Windows applications. It depends on how the developers of a certain Windows application coded it. Unfortunately many ignores interoperability: [http://ntfs-3g.org/support.html#posixfilenames2](http://ntfs-3g.org/support.html#posixfilenames2)

 
Windows can't handle all types of characters for filenames in folders, folder names and desktop files I was saying. Thought I was clear.

Thanks for the great program by the way. :) 

Nathan

---

### Post by szaka on 2008-01-11
You were clear but not right. It's perfectly possible to handle such files on Windows (see the explanation on the link I sent previously). Microsoft also explains this on her web pages and has a knowledgebase article how it's possible to delete such files on Windows (the issue is close to cause 6 but not exactly the same): [http://support.microsoft.com/kb/320081](http://support.microsoft.com/kb/320081) 

Such file names marked to be in the POSIX name space on NTFS, what the NTS-3G driver does of course, are 100% valid file names on Windows too. They could be handled by any Windows application. 

The problem would be if the file name were marked to be in the Win32 name space. That would be a corruption. The real problem here is that some Windows applications don't handle file names in the POSIX name space if they are not covered in the Win32 name space. But as the Microsoft example shows, they do could handle them. It would be just willingness and some minimal coding.

On the other hand, if Linux would limit the characterset used for file names then many POSIX program would break, sometimes resulting unrecoverable data loss.

---

### Post by ubuntu-freak on 2008-01-11
I guess I should have known you would get technical.
 
I was merely stating that you can't (by default) name files or folders with certain characters in windows as an error pops up. I've experienced it myself numerous times. I never attempted to get round it.
 
Nathan

---

### Post by fiddledd on 2008-01-11
> **szaka said:**
> You were clear but not right. It's perfectly possible to handle such files on Windows (see the explanation on the link I sent previously). Microsoft also explains this on her web pages and has a knowledgebase article how it's possible to delete such files on Windows (the issue is close to cause 6 but not exactly the same): [http://support.microsoft.com/kb/320081](http://support.microsoft.com/kb/320081) 

Such file names marked to be in the POSIX name space on NTFS, what the NTS-3G driver does of course, are 100% valid file names on Windows too. They could be handled by any Windows application. 

The problem would be if the file name were marked to be in the Win32 name space. That would be a corruption. The real problem here is that some Windows applications don't handle file names in the POSIX name space if they are not covered in the Win32 name space. But as the Microsoft example shows, they do could handle them. It would be just willingness and some minimal coding.

On the other hand, if Linux would limit the characterset used for file names then many POSIX program would break, sometimes resulting unrecoverable data loss.

I tried all the fixes posted at the above MS link, and also a few others, and have been able to rename/delete such files in the past. On this occaision however nothing I tried worked (apart from deleting the file in Ubuntu). This isn't really a problem if you just rename saved webpages rather than be lazy (as I was) and just save it with the page title. I should mention this is the first time I've been unable to delte the file in Windows (yes I did it before because I'm lazy) :)

---

### Post by Joeb454 on 2008-01-11
Why did you save it with illegal characters? :lolflag:

---

### Post by fiddledd on 2008-01-11
> **Joeb454 said:**
> Why did you save it with illegal characters? :lolflag:

As I said I'm lazy :) But also how often do people actually check all of the Web Page title for illegal characters before saving. Maybe Firefox or Ubuntu should have warned me, but i guess you can't be protected from yourself all the time.:)

---

### Post by Joeb454 on 2008-01-11
Nope your right, you can't.

Although I tend to rename most files so they make sense to me :)

---

### Post by jonnywombat on 2008-01-11
This explains a curious error I had recently. 

I had ripped a cd of music in ubuntu.. using sound juicers "online service" to name all the tracks appropriately..I  played it a few times in rythmnbox all was fine, and then I copied and pasted the cd folder to my windows partition.

Later I had to access windows, and when I tried to play the music one track would not play.. In the end I had a moment of inspiration and in ubuntu I re-named the track minus a question mark at the end.. and when i transfered it all was fine...

I could not work out why this was but I guess the error was caused in the same way.

Thanks for accidentally resolving that for me

Jonny

---

### Post by Joeb454 on 2008-01-11
There's a REALLY simple resolution to this - check for illegal file names before copying files to Windows. It'll save you a lot of trouble later on

---

### Post by ubuntu-freak on 2008-01-11
Can't believe I had to argue about it in my previous posts. 
 
Ah well...at least you guys jumped to my defense. Without even mentioning me mind. ;)
 
Nathan

---

### Post by Xavieran on 2008-01-11
[IDEA] Let's write a simple BASH script to remove illegal characters (sed,grep)!:)

PSEUDO CODE
I went to python...sry!
```

for files in os.listdir():
    find("illergal characters")
    somehow(replacethem)

```

---

