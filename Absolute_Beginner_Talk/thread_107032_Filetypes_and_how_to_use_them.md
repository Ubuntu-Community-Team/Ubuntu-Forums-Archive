---
title: "Filetypes and how to use them?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2005-12-22
Hiyas again.

Got another interesting question for you all...i hope. ;o) This should also be handy to a few other people also.

Just interested to know what filetypes there are out there and how to use/execute/install them.

I know .rpm files use the "alien" command.

.deb files use dpkg, and ".sh" use the sh command for shell scripts. Those are the basics i've learnt so far through trial and error.

Now how about the "tar.gz", "tar", ".run" filetypes? How would one use those? 

If somebody would be kind enough to perhaps do up a little howto about those filetypes and perhaps any others i'm unaware of, it'd be much appreciated. I'm sure a few others would also be interested in this also.

Regards
SW

---

### Post by codejunkie on 2005-12-22
[QUOTE=Stone_Wolf]Hiyas again.

Got another interesting question for you all...i hope. ;o) This should also be handy to a few other people also.

Just interested to know what filetypes there are out there and how to use/execute/install them.

I know .rpm files use the "alien" command.

.deb files use dpkg, and ".sh" use the sh command for shell scripts. Those are the basics i've learnt so far through trial and error.

Now how about the "tar.gz", "tar", ".run" filetypes? How would one use those? 

If somebody would be kind enough to perhaps do up a little howto about those filetypes and perhaps any others i'm unaware of, it'd be much appreciated. I'm sure a few others would also be interested in this also.

Regards
SW[/QUOTE]
the tar, tar.gz, tar.bz2, .bz2 packages are just like a .zip package there just compressed files that you have to extract and the .run files work like a shell script "sh nameoffile.run"
hope this helps.

---

### Post by bscbrit on 2005-12-22
These might be of help:

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-managing-file-types.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-managing-file-types.html)

[http://extensions.pndesign.cz/index.php?ext=a](http://extensions.pndesign.cz/index.php?ext=a)   (this is a list of _all_ known file extensions).

But you must also remember that linux doesn't use the file extensions - users do.  Linux employs a different method than Windows; in the latter the file extension is essential otherwise Windows does not know what to do with the file.  Linux has, in my opinion, a much more 'intelligent' approach.  It looks at the data and in most cases identifies what the data is for and opens the appropriate tool for the job.  Therefore you can install programs from files that have no extension in many cases.

Try this:  create an archive (.zip, .tar.gz or  .tgz).  Delete the extension.  Click on it. It opens!  If you want a nice warm feeling, repeat the experiment in Windows!

In a terminal type 'man magic'.

Use google to search for 'linux magic numbers' for more interesting reading.

---

