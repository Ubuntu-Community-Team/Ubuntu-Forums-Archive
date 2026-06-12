---
title: "Rhythmbox keeps adding Thumbs.db files"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-06-25
My Rhythmbox keeps adding the Thumbs.db files from my windows partition, where my songs are located. Is there any way to omit all the thumbs.db files from the library?, I select them all click remove, and almost everytime i start up rhythmbox, I have some more that are back. Any help would be awsome. :-)

---

### Post by Rocket2DMn on 2007-06-25
I use rhythmbox for music on my windows partition, but i haven't experienced (or noticed) this problem.  Have you checked the Preferences to see if you can filter file types that rhythmbox imports by default?

---

### Post by Bohlio on 2007-06-25
No there isnt any option for that. I think i have it because the Zune Software creates the album art in the same folder as the music, and if you browse it in explorer via thumbnail view, Windows creates the thumbs.db file. I suppose i could just flat out delete them, they aren't crucial files for windows and they get recreated whenever i browse my library in explorer, or so i think. If anyone else thinks otherwise, please tell me because i am not 100% sure.

---

### Post by Rocket2DMn on 2007-06-25
I'll try and find the time to look into my configuration when I get home later this evening and see if I can find anything to help.  In the meantime, if anybody else has input, please give!

---

### Post by muguwmp67 on 2007-06-25
thumbs.db is a file created by Windows, is it possible that you are browsing some of these folders from windows?

If you are using Windows, try this:
[http://www.ofzenandcomputing.com/zanswers/98](http://www.ofzenandcomputing.com/zanswers/98)

---

### Post by Bohlio on 2007-06-25
Yes, I do occasionally browse the my music files from explorer, but i never knew that you could get rid of the thumbs.db files, I guess all i gotta do is "Check off the circle next to Do not cache thumbnails" while under windows and they will all go away :-) Hopefully it deletes them all instead of just ceasing to create them. Once again, thanks for the link, Ill have to weed out the files under windows in order to get rid of them in ubuntu :-P

---

### Post by Rocket2DMn on 2007-06-25
OK, I didn't find any settings for file types either, but it looks like you have the solution.  If you want to make your life easy deleting the existing thumbs.db files, just run the commands:
```
cd /path/to/music/folder
rm -R *.db
```
I use a * because I think sometimes the T is capitalized in thumbs (or maybe that's desktop.ini), but you get the idea.

---

### Post by Bohlio on 2007-06-25
thanks man :-) That will be great if windows doesnt automatically delete the files after I uncheck the cache thumnails option. Thank you very much.

---

