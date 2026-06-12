---
title: "imagemagick resize help"
date: 2007-04-22
forum: Art &amp; Design
---

### Post by steharg on 2007-04-22
i am trying to resize a load of images so they are no more than 150x150px

i am currently using

```
convert -resize 150x150\> *.jpg
```

but it is renaming all the files to that of the last image then adding a number after each one...
lastfilename.jpg.1
lastfilename.jpg.2
etc

how can i get it to keep its original file name? or even go back over to rename it without the numbers on the end?

---

### Post by steharg on 2007-04-22
sussed it out

needed to use the mogrify command instead which overwrites the original file

```
mogrify -resize 150x150\> *.jpg
```

about a million times quicker than photoshop!

---

### Post by FuturePilot on 2007-04-23
Wow! This will come in handy for quick resizing of pictures instead of doing it through Gimp. This is why I love Linux. I've been using Ubuntu for almost a year and I'm still discovering little things like this that amaze me.

Thanks for sharing that.
:guitar:

---

### Post by bashologist on 2007-04-23
Maybe try this:
```
for img in *.jpg; do convert -resize 150x150 "$img" "$img"; done
```

---

### Post by Jonne on 2007-04-24
How would you rename the resulting file? 

I'd like to have the first file be called 1.jpg, the second 2.jpg, etc. Is there a way to find out which iteration you're in?

---

### Post by bashologist on 2007-04-26
Sorry for the slow reply, almost didn't see it.

# To shrink the file and get a new name in the fromat 001.jpg, 002.jpg ...:
c=1; for i in *.jpg *.JPG; do [ ! -f "$i" ] && continue; r=$(printf "%03d" "$c"); convert -resize 150x150 "$i" "$r.jpg"; ((c++)); done

# To shrink the file then delete the old file with rm "$i":
c=1; for i in *.jpg *.JPG; do [ ! -f "$i" ] && continue; r=$(printf "%03d" "$c"); convert -resize 150x150 "$i" "$r.jpg"; ((c++)); rm "$i"; done

# To just rename files in the format 001.jpg, 002.jpg ...:
c=1; for i in *.jpg *.JPG; do [ ! -f "$i" ] && continue; r=$(printf "%03d" "$c"); mv -i "$i" "$r.jpg"; ((c++)); done

---

### Post by Jonne on 2007-04-26
I'd already found a way by using a temp variable and incrementing it in every loop (which is basicly what you did too). My code is more verbose but it works. I'll try your version though, as it looks like you know your bash ;).

I was just confused that there was no way to do the equivalent of 
```
for(i=0;i<array.length;i++)
```
where you can use i to find out which iteration you're in.

Now I just need to add the smb share where the pdf's are to fstab, write some code to copy the files over from the smb share. I hope I'll be able to manage that :). Thanks for your help.

---

