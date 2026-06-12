---
title: "Open Office not recognizing .doc files"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by modestglock26 on 2007-11-03
So I can't really figure out what's going on with my Open Office. I was using it the other day in a class and saved my work as a .doc file type. 

Tonight I was having issues with my computer reinstalled Ubuntu 7.10. I loaded all my saved docs from my back up hard drive and now Open Office isn't recognizing the .doc files that I had originally created through it.

I am new to Ubuntu and linux so I am sorry for the noob question, however...I really need to be able to access these documents. 

What can I do to get them back?

Thanks


PS. I have tried uninstalling OO and putting back in so I'm not really sure what else to try.

---

### Post by modestglock26 on 2007-11-03
So I can't really figure out what's going on with my Open Office. I was using it the other day in a class and saved my work as a .doc file type.

Tonight I was having issues with my computer reinstalled Ubuntu 7.10. I loaded all my saved docs from my back up hard drive and now Open Office isn't recognizing the .doc files that I had originally created through it.

I am new to Ubuntu and linux so I am sorry for the noob question, however...I really need to be able to access these documents.

What can I do to get them back?

Thanks


PS. I have tried uninstalling OO and putting back in so I'm not really sure what else to try.

---

### Post by Nikitas350 on 2007-11-03
If you can attach a ".doc" file to see if the problem is in the computer or on the file...

---

### Post by Incense on 2007-11-03
Will it open any kind of files? You can install abiword from the repo, it can handle Doc files as well, so you have access to them. 

```
sudo apt-get install abiword
```

---

### Post by modestglock26 on 2007-11-03
Well I am now intalling abiword to see what happens. Last night I couldn't get OO to open any of the .doc files that I originally wrote on OO. 



I just tried Abiword and it is also saying the file is not valid.

I also just tried to upload a file to share and the uploads keep failing. Im guessing OO isn't to blame now, but it makes no sense to me that I used OO to create the files but now its saying they are invalid.

Confused.

---

### Post by forestpixie on 2007-11-03
> I also just tried to upload a file to share and the uploads keep failing

there's a file size limit - make sure it's small enough.

If you get one up I'll see if I can open it, alos it might be worth posting the actual error you get here

Edit - also check that oo is opening other files as Incense asked

---

### Post by modestglock26 on 2007-11-03
error in OO
Cannot open 11-1-07 Class notes.doc
The filename "11-1-07 Class notes.doc" indicates that this file is of type "Word document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

I just tried putting these files on a computer running XP and they open blank in MS Office 03

---

### Post by modestglock26 on 2007-11-03
here is the Abiword error:

AbiWord cannot open /home/casey/Desktop/HIST/11-1-07 Class notes.doc. It appears to be an invalid document

---

### Post by haldean on 2007-11-03
When you say it doesn't recognize the files, do you mean that it won't open them when you go to File -> Open, or does it not open OpenOffice when you double click the file in Nautilus?

---

### Post by modestglock26 on 2007-11-03
Okay so I just googled a .doc file to see what I could get. All the stuff on my computer was written with OO so none of it now shows up on any computer. The sample file I just got opened perfect in OO.

I guess all my school work is now gone?

---

### Post by forestpixie on 2007-11-03
have you got one small enough to upload

---

### Post by chunderbunny on 2007-11-03
Sounds like your document has become corrupted and has the wrong MIME-type. 

Unfortunately I don't know how to fix MIME information, but you could try renaming the .doc to a .txt, .odt or .rtf format to see if to will open then. If it works, copy the text to a new document and save it.

---

### Post by modestglock26 on 2007-11-03
> **haldean said:**
> When you say it doesn't recognize the files, do you mean that it won't open them when you go to File -> Open, or does it not open OpenOffice when you double click the file in Nautilus?

When I try to open using the File>Open technique I get those errors. I hate to say it but I don't know how to use Nautilus.

I am new to this platform and it was suggested by a friend and some co-workers. Everything was great until last night.

Is there a different way I should be trying to access these files?

---

### Post by modestglock26 on 2007-11-03
> **forestpixie said:**
> have you got one small enough to upload


No I just went thru them all and they are too big.

---

### Post by modestglock26 on 2007-11-03
> **chunderbunny said:**
> Sounds like your document has become corrupted and has the wrong MIME-type. 

Unfortunately I don't know how to fix MIME information, but you could try renaming the .doc to a .txt, .odt or .rtf format to see if to will open then. If it works, copy the text to a new document and save it.


It is pulling up blank in all of the mentioned formats. I was hoping this would have worked. I tried going to .odt last night and nothing happened. I just tried the rest and all just give me blanks.

---

### Post by forestpixie on 2007-11-03
what about renaming a backed up one - or is that what you're working with

---

### Post by modestglock26 on 2007-11-03
I just got done pulling them off my external and tried. 

No luck.

This sucks. I thought I was doing myself a favor by saving them in the MS format but I think if I keep using OO I will be keeping them in .odt and just dealing with it. I guess if I need to I can alway do a Save As and make a copy in a diff. format.

---

### Post by forestpixie on 2007-11-03
have to say that's what I do - save everything as opeoffice format and do a save as 

sorry that I'm not able to help more

---

### Post by modestglock26 on 2007-11-03
> **forestpixie said:**
> have to say that's what I do - save everything as opeoffice format and do a save as 

sorry that I'm not able to help more

No thats okay I do appreciate all the help. I think I have learned a lesson in the process and I thought backing up my data to an external would solve most of my issues but new ones always come up. 

I think I know what I'll be doing with the rest of my weekend.,,

Re-typing all my term papers and notes.........

---

### Post by forestpixie on 2007-11-03
as an aside you could try looking on the openoffice forum - try a thread there - might help

---

### Post by Incense on 2007-11-03
> **forestpixie said:**
> as an aside you could try looking on the openoffice forum - try a thread there - might help

I was going to suggest this as well. They have fantastic forums over there. Sorry to hear about your experience. I have created a lot of files in writer, and even saving as DOC have never had these kind of problems. I hope you don't turn away from the open source world because of this. I personally save my files as ODF, then DOC so I have two copies, one native, and one for the MS folks. If I really need something out there, then I'll save it as a PDF. I hope you can recover your data. Good luck!

---

### Post by Nikitas350 on 2007-11-06
If you want you can mail me a .doc file to [email]nikitas@c-lab.gr[/email] and then i will test it. Don't give it up... ;)

---

### Post by mike555 on 2007-11-06
You might also try uploading it to a conversion service like ...
[http://trial.3bview.com/3BTrial/pages/opendoc.jsp;jsessionid=09F691851B29D778306B1DB0D3ED6A3E](http://trial.3bview.com/3BTrial/pages/opendoc.jsp;jsessionid=09F691851B29D778306B1DB0D3ED6A3E)   
  maybe they can figure it out .........

---

### Post by modestglock26 on 2007-11-06
Just wanted to let ya'll know that this has in no way turned me away from anything open source and I am still sticking with Ubuntu. I can't really explain what happened in this case but I'm just gonna leave it as "Operator Dumbness" for now. My teachers have been helpful with getting me back some lecture notes so I am just trucking along. 

I will say that after I reinstalled Ubuntu it is running better than it was before. My touchpad scrolling was all slow and jumpy before and now its perfect.

OO is working well and I got another thumbdrive to dump my school stuff onto while I'm in class so hopefully I wont have this issue again.

Thanks, and I'll check the links out as well.

Casey

---

