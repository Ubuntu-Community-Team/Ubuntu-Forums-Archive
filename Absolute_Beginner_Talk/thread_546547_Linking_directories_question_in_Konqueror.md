---
title: "Linking directories question in Konqueror"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-09-09
Hi all...Using Kubuntu Feisty and Konqueror.

I used the following to create a shortcut **in** my "music" directory **to** my "documents" directory 

ln -s ~/documents ~/music

And then I did the reverse by creating a shortcut **to** my "music" directory **in** my "documents" directory

ln -s ~/music ~/documents

Now when I open ~/documents I see a link to ~/music. If I click on the link I end up in ~/music and see a link to ~/documents. If I click on that link I'm back in ~/documents and see a link to ~/music. If I click on that link.....etc etc and round and round we go in a never-ending circle.

My question (finally) is why does Konqueror report my location as.....
~/docs/music/docs/music/docs/music

I understand that, technically, that's where I am but I'm actually only in either ~/documents or ~/music. How can I make Konqueror say that in the location bar.

Thanks
Miguel

---

### Post by GMachine_24 on 2007-09-09
I believe it's because Konqueror is giving you the actual path by which you arrived at your final destination. Every time you click on a line to, say, your music file, Kubuntu is opening a new music folder; same when you click on your directory link. I'm guessing you end up with five or six actual folders open, layered on top of each other..and you must close all of them individually..........unless you do a kill all or something.

Of course, I could be wrong. But one thing about Linux is it has a very linear, logical way of doing things and at the end you are, as I said before, actually in the third music folder that is open. You could play this out forever but that would seem pointless.

 I just tried this on my Ubuntu Edgy comp and ended up with a completely different result. If i createa symbolic link from /music to /PDF and then try to create a symbolic link from /PDF to music, I end up with a link to /PDF in BOTH folders. In other words, I can't go from /PDF to /music . . . I guess I'm not giving the proper command or what not.

I know this probably hasn't been helpful. But I figure more information might be better at some point.

--gm

---

