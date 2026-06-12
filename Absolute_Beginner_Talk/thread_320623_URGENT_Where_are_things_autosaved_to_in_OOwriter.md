---
title: "URGENT: Where are things autosaved to in OOwriter?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by c0rd3l1a on 2006-12-17
My final was due yesterday and I turned it in, but my prof wrote back to inform me that I'd turned in a paper that was not nearly finished. Now when I try to find my finished paper (that I finished Saturday night), it is nowhere to be found. I have no idea what happened to it. In order to replace it, I need to know where OpenOffice.org Writer saves things when it autosaves them. That is my last hope. Otherwise, I'll be rewriting and penalized for being late...

---

### Post by bugzor on 2006-12-17
/home/[username]/.openoffice.org2/user/backup

---

### Post by c0rd3l1a on 2006-12-17
I don't have any kind of openoffice folder under my username.

---

### Post by mdsmedia on 2006-12-17
in Nautilus (assuming you're using Ubuntu) under your /home/username/ folder, press ctrl-H (to view hidden folders and files). Folders with a . in front of their names are hidden folders so you can't see them immediately.

---

### Post by c0rd3l1a on 2006-12-17
Thank you so much for explaining that! However, now that I can find the folder, I see that it is empty =[ I guess I have to spend the rest of tonight rewriting my paper. I'm on the OpenOffice.org forums trying to figure out why this happened.

---

### Post by mdsmedia on 2006-12-17
Did you not save your paper before you submitted it? If so, you need to find where you saved it to. If you're not sure where you saved it to, an idea would be to go into OOo, create a document, click on File SaveAs and see where the file is going to be saved to. That's probably where you saved it to.

I'm guessing that for some reason you can't find a saved file, though.

---

### Post by c0rd3l1a on 2006-12-17
Yes, I'd been saving it to my desktop. The file that is currently on my desktop only shows evidence of having been saved Friday night; it doesn't include anything that I saved all day on Saturday. OOwriter had been autosaving every few minutes and I had been ctrl+s saving every 5 minutes the entire time I'd been working on it on Saturday. I File>Saved when it was finished, before closing the program. I didn't receive any error messages at any point in the process and OOwriter didn't crash at any point either. This is so frustrating! I hope that someone on the OpenOffice.org forum can clue me in as to what happened and how to prevent it in the future because not knowing what caused this is going to make me far more anxious every time I write a paper =-/

---

### Post by zekopeko on 2006-12-17
did you try looking for hidden files on the desktop? i don't know if this is the case with OOw
but when i click on my desktop and then do ctrl+h there are usually some files like:

NameOfFile~.txt 

perhapse it's there

---

### Post by mdsmedia on 2006-12-17
> **c0rd3l1a said:**
> Yes, I'd been saving it to my desktop. The file that is currently on my desktop only shows evidence of having been saved Friday night; it doesn't include anything that I saved all day on Saturday. OOwriter had been autosaving every few minutes and I had been ctrl+s saving every 5 minutes the entire time I'd been working on it on Saturday. I File>Saved when it was finished, before closing the program. I didn't receive any error messages at any point in the process and OOwriter didn't crash at any point either. This is so frustrating! I hope that someone on the OpenOffice.org forum can clue me in as to what happened and how to prevent it in the future because not knowing what caused this is going to make me far more anxious every time I write a paper =-/
I'd probably spend some time searching for your document. If you were saving it all day Saturday I'd reckon it must be saved somewhere, but just not where you think it should be.

I'm not saying it's not possible for files to disappear but it is probably more likely that the document is saved somewhere you don't expect. If you find it, most of your work will have been done :)

Good Luck :)

---

### Post by JNowka on 2006-12-17
May I suggest using Places->Search for Files  and changing the Look in folder option to Filesystem.  Then type in the name of the file.  It may find it for you.  You can also try something like *.doc or whatever file type you use in the search perimiters and see if there are any file last saved a couple days ago.

---

### Post by c0rd3l1a on 2006-12-17
I tried all of these suggestions, to no avail. I did Places>Search for Files and searched the filesystem for every single file modified in the last 3 days. The OpenOffice.org backup folder showed up, but it was empty. According to that, the last time my document was modified was about 1am Saturday morning. But I modified it, heavily, all day on Saturday, ending around 8pm. This must be some kind of bug with OpenOffice.org where the autosave and ctrl+s save features sometimes just don't actually do what they say they do.
I have to give up on the search now so that I can start rewriting my paper. ](*,) ](*,) ](*,) 

Thank you all very much for your help, though!

---

### Post by macogw on 2006-12-17
try 
```

ls -a ~/Desktop
```
and see if it shows the file with a ~ after it.

---

