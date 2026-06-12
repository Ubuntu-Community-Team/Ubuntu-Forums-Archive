---
title: "help: adding missing extensions to file names"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2006-11-30
I have several temp files in mp3 format that I cannot play in a media player until I add ".mp3" to the end of each file name. Is there a script or command ,etc that I can use to accomplish this. For now, I am having to right click on each file and rename it with .mp3 at the end.

---

### Post by gborzi on 2006-11-30
You can use the following command to add a .mp3 extensions to all files in a dircetory: > for i in *; do
mv -i $i $i.mp3
done
note that this command will add a .mp3 extension to those files that already have it, i.e. a file name song.mp3 will be renamed song.mp3.mp3.

---

### Post by deadgobby on 2006-11-30
> **randytuggle said:**
> I have several temp files in mp3 format that I cannot play in a media player until I add ".mp3" to the end of each file name. Is there a script or command ,etc that I can use to accomplish this. For now, I am having to right click on each file and rename it with .mp3 at the end.
 Are you copying a CD or DL from the net? Does it say for sample song.mp3OK?

---

### Post by randytuggle on 2006-11-30
> **gborzi said:**
> You can use the following command to add a .mp3 extensions to all files in a dircetory: 
note that this command will add a .mp3 extension to those files that already have it, i.e. a file name song.mp3 will be renamed song.mp3.mp3.

That worked beautifully! Thanks to you! You're a guru of Ubuntu! :)

---

### Post by an.echte.trilingue on 2006-11-30
for future reference, cp and mv include suffix switches that you can use instead.

---

### Post by IYY on 2006-11-30
Also, there is a command called file, that checks what type the file really is. So, if you have a file with no extension called somefile, you could check its type with:

```
file *somefile*
```

It's also possible to incorporate this command into large scripts that would go through all of your files, and append the .mp3 suffix for those files that truly are of mp3 type.

---

