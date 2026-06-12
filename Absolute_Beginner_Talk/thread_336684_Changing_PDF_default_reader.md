---
title: "Changing PDF default reader"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-01-11
How can I make Acroread the default PDF reader? 
The default is now Evince which won't print single pages or pages within a range.
Can I just remove Evince?
I'm using Edgy Eft.
Thanks

---

### Post by meng on 2007-01-11
Right click on any PDF file, go to Properties, Open With.

---

### Post by Stunt Double on 2007-01-11
In OPEN WITH, I can add Adobe Reader but I can't de-select Open Folder which must be Evince? And I can't select Adobe Reader even though it is at the top. 
I still have to select Adobe Reader every time I open a folder.
I would completely remove Evince but there is also Evince Thumbnailer which may do something useful and which may need Evince to function.
When I open picture files, whichever thumbnailer does it, it's remarkably fast. I had previously thought it was gThumb ImageViewer but the thumbnail format is different.
Does Evince Thumbnailer need Evince?

---

### Post by jem7v on 2007-01-12
Yeah, Meng didn't really answer your question.

Right click on a .pdf and choose **Properties**.  Go to the Open With tab, and there will be a list of programs that can open .pdf files.  Check off the one you want to be the DEFAULT, and close the dialogue window.  That will change the default instead of just opening it in a different program one time.

---

### Post by Quillz on 2007-01-12
You should be able to remove Evince, so long as it isn't a core component of GNOME. Just "sudo apt-get remove evince" should do it.

---

### Post by Stunt Double on 2007-01-12
Problem is that I can't check off Acrobat Reader. And Open Folder can't be unchecked. Must be a glitch.

---

### Post by Stunt Double on 2007-01-12
Problem solved.
I used   sudo apt-get remove evince   to remove Evince. It also removed Evince-thumbnailer at the same time. The thumbnailer for jpg pictures was unaffected. Now Adobe Reader opens PDF files every time.
Thanks for the help Meng, jem7v, and Quillz.

---

### Post by Quillz on 2007-01-12
> **Stunt Double said:**
> Problem is that I can't check off Acrobat Reader. And Open Folder can't be unchecked. Must be a glitch.
Are you sure you're linking to the executable? IIRC, there are several directories that contain Reader files. Generally speaking, the actual programs tend to be in /bin/, /usr/bin/ or /opt/

---

### Post by Delkster on 2007-01-12
> **Stunt Double said:**
> Problem is that I can't check off Acrobat Reader. And Open Folder can't be unchecked. Must be a glitch.

Uh, PDF files shouldn't have "Open Folder" as an option. That's just for folders. Are you sure you were looking at the properties of a PDF file, not a folder?

---

### Post by Stunt Double on 2007-01-12
It WAS my error. The actual PDF file was one more click forward. That does explain it. Thanks.

---

