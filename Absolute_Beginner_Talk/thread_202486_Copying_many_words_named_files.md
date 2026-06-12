---
title: "Copying many words named files ?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by igrachev on 2006-06-23
Hello i guess the answer to my question is easy but i cant solve the problem by myself so i will ask well here it is i want to copy some files from my win ntfs partitions but their mane is not one whole string of simbols (like Metallica - Unforgiven) so the shell didnt understand the spaces and shows an error(cp: missing destination file operand after ... ) so who can i copy such files whitch name is more than one word ?

---

### Post by henderb on 2006-07-20
You can use "\ " to type a space. ("\" "escapes" characters so that they have a different meaning. In this case, it makes it a space rather than an argument separater on the shell.)

---

### Post by muep on 2006-07-20
You can also just put quotation marks around the filenames, like this:

cp "music/A great song.ogg" ~/music/

---

### Post by BoyOfDestiny on 2006-07-20
If you are working from terminal, tab completion also works well.

Just put the first part hit tab, if there are similarly named files hit it twice and it will help you narrow it down. 

If you'd rather copy the files en masse,

cp *.mp3 ~/music

Would copy the mp3s in the current directory to music in your home directory.

if you want to do it by directory

cp -r mysong ~/music

Would copy the dir myson to your music folder

---

