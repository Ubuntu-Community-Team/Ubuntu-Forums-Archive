---
title: "Inheritable permissions in a directory?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-19
As those of you who have been following my progress may have guessed, I finally got my partitions created to my liking. Now I'm in the process of transferring my files from my XP box to my Ubuntu box. Needless to say some interesting things have been happening with permissions. I started with my Music collection by just creating a directory in the HOME folder named Music, gave myself full permissions on it and started copying the files over from an NTFS-based network share. When I was done I was shocked to find that the permission set on the Music directory did not inherit down to its contents (my music collection). I wound up spending quite a bit of time changing those permissions manually. I know that Windows has an option to allow files and folders copied to a parent directory to “Inherit” its permission set. 

I was just wondering if a similar feature exists fore EXT3 Directories and if so how would I enable it (or apply it to a group of subfiles and subdirectories)?

---

### Post by aysiu on 2006-06-19
[This](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) may help.

---

### Post by ZeusABJ on 2006-06-20
[QUOTE=aysiu][This](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) may help.[/QUOTE]

Ah yeah... you gave me that link the other night didn't you Aysiu?

#-o 

Sorry!

---

### Post by Ptero-4 on 2006-06-20
Type this:
```

sudo chown -R user:group ~/Music

```

And everything in your Music folder will have the permissions you want.

---

### Post by ZeusABJ on 2006-06-20
Thanks I'll try that.... but hey (just to clarify), where it says "user" and "group" in your command, am I supposed to substitute my username and group?

---

### Post by Ptero-4 on 2006-06-21
Yes.

---

### Post by ZeusABJ on 2006-06-21
[QUOTE=Ptero-4]Yes.[/QUOTE]
Sweet, thanks!

---

