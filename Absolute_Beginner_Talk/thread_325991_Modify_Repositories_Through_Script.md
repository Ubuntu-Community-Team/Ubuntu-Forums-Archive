---
title: "Modify Repositories Through Script"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by nhandler on 2006-12-26
I am trying to put together a script that will take care of the initial setup of Ubuntu (Update Repositories, Update and Install Programs, Change settings, etc). Is there any easy way to go about enabling the extra repositories in Ubuntu using the terminal? Or is there a way to put tell the script to create a file and add the repository content it automatically?

I guess what I'm trying to say is, how can I add extra repositories using a script?

---

### Post by po0f on 2006-12-26
Cheater,

```
[FONT="Courier New"]$ sudo echo 'deb http://myrepo.com/ubuntu edgy blar' >> /etc/apt/sources.list[/FONT]
```
The double '>' are important; these tell echo to append to a file (actually, they tell bash to append).  If it was a single '>', it would erase the contents of the file, replacing it with whatever you echo'ed.

[EDIT]

Make sure you use double '>', I can't stress this enough.  :)

---

### Post by nhandler on 2006-12-26
> **po0f said:**
> Cheater,

```
[FONT="Courier New"]$ sudo echo 'deb http://myrepo.com/ubuntu edgy blar' >> /etc/apt/sources.list[/FONT]
```
The double '>' are important; these tell echo to append to a file (actually, they tell bash to append).  If it was a single '>', it would erase the contents of the file, replacing it with whatever you echo'ed.

Thanks a lot po0f. Is there a way to append/overwrite the file with multiple lines (other than running the command multiple times)?

---

### Post by po0f on 2006-12-26
Cheater,

I suppose you could use `sed`, but I forgot how to detect EOF.  Or you could do one really big echo:
```
[FONT="Courier New"]$ sudo echo "line1\nline2\nline3" >> /etc/apt/sources.list[/FONT]
```
The above *should* work.  Note that those are double quotes, not single quotes.

---

### Post by nhandler on 2006-12-26
> **po0f said:**
> Cheater,

I suppose you could use `sed`, but I forgot how to detect EOF.  Or you could do one really big echo:
```
[FONT="Courier New"]$ sudo echo "line1\nline2\nline3" >> /etc/apt/sources.list[/FONT]
```
The above *should* work.  Note that those are double quotes, not single quotes.

Thanks a lot. I just converted all the line breaks to \n for my sources.list. It wasn't that hard. I can live without sed.

---

