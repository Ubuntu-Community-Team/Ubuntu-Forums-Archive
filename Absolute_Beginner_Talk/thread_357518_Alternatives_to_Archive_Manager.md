---
title: "Alternatives to Archive Manager"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-02-09
I'd like to do something that I suspect is not possible with Archive Manager, namely, select multiple .zip files (say, 100 or more) and do "extract here" with all of them at once. Can anyone recommend an alternative app that can do this?

Also, as long as I'm asking, is there a download manager that is generally regarded as "The Best"? Thanks in advance.

---

### Post by po0f on 2007-02-09
ricardisimo,

Are you opposed to using the terminal for this?  If not, either of the following should work:

```
[FONT="Courier New"]$ unzip *.zip
$ for file in `/bin/ls *.zip`; do unzip $file; done[/FONT]
```

If you need to select ZIP files from multiple directories, or if you want to extract them to different directories based on criteria like the filename, post back and we'll see if we can't get something working.

---

### Post by ricardisimo on 2007-02-09
I'm having difficulty spotting the variables in the formula here. Is "/bin/ls" my directory? Or am I dragging and dropping the lot of them somewhere into your code?

---

### Post by po0f on 2007-02-09
ricardisimo,

The `/bin/ls *.zip` portion of the for statement just returns a list of all the files in the current directory that end in '.zip'.

---

### Post by ricardisimo on 2007-02-09
OK, so first I have to navigate terminal to the folder in question, then your code, correct?

---

### Post by po0f on 2007-02-09
ricardisimo,

Yes, that is correct.  :)  I'm sorry, I should have been more specific.

---

### Post by ricardisimo on 2007-02-09
Don't apologize for anything. I'm the dimwit here. Thanks again. :)

---

### Post by ricardisimo on 2007-02-09
Worked perfectly! Just curious - what is the first line supposed to do? All I got was a long series of error messages like so:
```
caution: filename not matched:  twic625g.zip
caution: filename not matched:  twic626g.zip
caution: filename not matched:  twic627g.zip
caution: etc., etc., etc....
```

---

### Post by po0f on 2007-02-10
ricardisimo,

Are you talking about the `unzip *.zip` command?  Yeah, I didn't think that one would work.  It's probably looking for files named twic625g.zip, twic626g.zip, twic627g.zip...  in whatever file the first one evaluated to be.  So for:

```
[FONT="Courier New"]$ ls
1.zip 2.zip 3.zip 4.zip
$ unzip *.zip[/FONT]
```

the unzip command would look for files named 2.zip, 3.zip and 4.zip *inside* 1.zip, since the shell would expand the '*.zip' to all the files ending in the .zip extension, then pass them along to the `unzip` command, before the unzip command would even know what its arguments were.  Pretty much, I didn't RTFM before I posted that command.  I'm glad the second one worked for you though.  :)

---

