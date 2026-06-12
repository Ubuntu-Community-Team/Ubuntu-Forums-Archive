---
title: "Abbreviated Path/Filename"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-12-20
G'day.

I'm trying to remove a file from .Trash.
When I click Empty Trash in the GUI I get this:

Error while deleting.
"/home/rich/.../gspca.mod" cannot be deleted because
you do not have permission to modify its parent folder.

And so far I have done this:

rich@rich-laptop:~$ cd ~/.Trash
[email]rich@rich-laptop:~/.Tras[/email]h$ locate gspca.mod
/home/rich/.Trash/...gspca.mod
/home/rich/.Trash/...gspca.mod/.tmp_versions
/home/rich/.Trash/...gspca.mod/.tmp_versions/gspca.mod
[email]rich@rich-laptop:~/.Tras[/email]h$ ls -a
 ...gspca.mod
[email]rich@rich-laptop:~/.Tras[/email]h$ rm ...gspca.mod
rm: cannot remove `...gspca.mod': Is a directory
[email]rich@rich-laptop:~/.Tras[/email]h$ rm gspca.mod
rm: cannot remove `gspca.mod': No such file or directory
[email]rich@rich-laptop:~/.Tras[/email]h$ 

When I include the dots ->...<- in the filename, it tells me it's a directory and can't be deleted.
When I exclude the dots, it tells me the file does not exist.

Two questions:
1. How can I know the full path/filename for this file?
2. Why is the full path/filename abbreviated with dots ... ?

Thanks much,
Rich

PS: I understand I don't have permission to delete it. Once I know the full path/filename I'll be able to chown and rm.  Thanks.

---

### Post by nhandler on 2007-12-20
The full path of the file is:
"/home/Rich/.Trash/...gspca.mod"
However, that file is in fact a directory. Remove it with this command:
```
rm -rf /home/Rich/.Trash/...gspca.mod
```
I don't know why it has 3 dots in its name. A folder/file beginning with 1 dot is hidden and not displayed by default in nautilus or by ls. There is no reason to have 3 dots.

Also, if you get an error saying you don't have permission to delete the folder when you run the command above, try putting sudo in front of it. That will run it as root.

---

### Post by RichPicker on 2007-12-20
Here's the result:

[email]rich@rich-laptop:~/.Tras[/email]h$ cd
rich@rich-laptop:~$ rm -rf /home/Rich/.Trash/...gspca.mod
rich@rich-laptop:~$ cd ~/.Trash
[email]rich@rich-laptop:~/.Tras[/email]h$ ls -a
.  ..  ...gspca.mod

It's still there.

I copied and pasted that filename, with all the dots in front of it, and got this:

rich@rich-laptop:~$ rm -rf /home/Rich/.Trash/.  ..  ...gspca.mod
rm: cannot remove `.' or `..'
rm: cannot remove `.' or `..'
rich@rich-laptop:~$ 


Rich

---

### Post by RichPicker on 2007-12-20
Check this out:

rich@rich-laptop:~$ cd ~/.Trash
[email]rich@rich-laptop:~/.Tras[/email]h$ ls -lt
total 0
[email]rich@rich-laptop:~/.Tras[/email]h$ ls -a
.  ..  ...gspca.mod


It's got be baffled.

---

### Post by Taboo Mirage on 2007-12-20
```
rm -rf ~/.Trash/*
```

---

### Post by SOULRiDER on 2007-12-20
If it complains about not being able to remove files due to permission restrictions you will have to add sudo, making ti looks like this:
```
sudo rm -rf ~/.Trash/*
```

---

### Post by RichPicker on 2007-12-20
Here is is:

rich@rich-laptop:~$ rm -rf ~/.Trash/*
rich@rich-laptop:~$ cd ~/.Trash
[email]rich@rich-laptop:~/.Tras[/email]h$ ls -a
.  ..  ...gspca.mod
[email]rich@rich-laptop:~/.Tras[/email]h$ 

It's still there.

---

### Post by PeterJS on 2007-12-20
Try stepping it up a bit, and empty the trash by getting rid of it all together.
```

rm -rf ~/.Trash

```
Your file manager will recreate the ~/.Trash folder automatically next time it's needed.

---

### Post by RichPicker on 2007-12-20
I get this:

rich@rich-laptop:~$ rm -rf ~/.Trash
rm: cannot remove `/home/rich/.Trash/...gspca.mod/.tmp_versions/gspca.mod': Permission denied
rich@rich-laptop:~$ 

Someone suggested "touch .Trash" but said I should record the ownership and permissions for .Trash first. I have no idea how to record that.

---

### Post by RomeReactor on 2007-12-20
Hi. Try this approach: from the terminal:
```
gksudo nautilus ~/.Trash
```
when Nautilus shows up, press CTRL+H, highlight all the files and folders there and press DEL. Then close Nautilus.

---

### Post by RichPicker on 2007-12-20
That did it. YOU are a genius. :popcorn::KS:):guitar::p:D):P8)

Thank you very much.

Happy Holidays.

Rich

---

### Post by ncappel1 on 2007-12-20
This is off  topic, but I'd like to draw attention to how this is a functional use of "rm -rf" that won't destroy your system. A friend of mine was paranoid that he saw this post, he was reacting to everyone's signiture's that sound like a witch-hunt against the use of the command.

---

### Post by RichPicker on 2007-12-20
I was warned about using rm -rf along with the asterisk (*). As in rm -rf .Trash*

Off topic, yes. But it's fascinating. How dangerous would it have been for me to use 
touch .Trash    ?

---

