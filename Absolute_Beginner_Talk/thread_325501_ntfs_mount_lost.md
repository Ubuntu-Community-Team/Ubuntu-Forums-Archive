---
title: "ntfs mount lost"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by gregcha117 on 2006-12-25
I'm in need of some help from somoene.... i was in the middle of downloading a dvd on my mounted windows drive, and apparently i ran out of space, i tryed deleting some files and realized they just disappeared but no space was freed up and now i cant start windows xp, i just get a blue screen and the mounted drive disappeared from ubuntu :|

---

### Post by kidders on 2006-12-25
Hmm :-( Odd things can happen when you write to NTFS filesystems with Linux. Your best bet might be to boot your PC from a Windows boot disc and go from there.

It's possible that your Ubuntu system logs might give you some clues about what the problem is ... but they're often a little vague and unhelpful when things go wrong with filesystems.

---

### Post by gregcha117 on 2006-12-25
well you can ignore that first part but there is one thing i need to know (for whatever reason it fixed itself and its remounted)

everytime i try to delete from the drive it deletes the file, but no space is freed? any idea how i can fix this/where the files are actually going ?

---

### Post by kidders on 2006-12-25
That's odd! Is that to say that if you open a terminal and "rm" something, doing a "df" shows no change?

---

### Post by gregcha117 on 2006-12-25
not sure what that means :P but i found where they were giong, they end up in a folder on the ntfs drive called ".trash-greg" is there anyway that i can make them goto the regular trash can so i dont have to navigate to that hidden folder and delete them everytime i want to delete a file ?

---

### Post by kidders on 2006-12-26
Deleting something and "trashing" it aren't the same thing ... if you trash something, you won't save any disk space, since all you're really doing is moving it around. I imagine that if you delete stuff, it will vanish though.

---

