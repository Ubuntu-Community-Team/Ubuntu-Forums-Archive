---
title: "Par-N-Rar for linux (verify, unrar and remove)"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Blinkiz on 2008-02-06
**Background**
[Par-N-Rar]("http://www.milow.net/public/projects/parnrar.html") is a graphical utility which accepts a directory as input and will repair/verify any PAR/PAR2/SFV/MD5 files in that directory. Once it verifies a set of files, it will attempt to unRAR them. Once it finishes unRARing a RAR archive, it will (optionally) remove the original PAR/RAR files.

**Goal**
[list=1]
[*]I want to have a utility that will scan directory/subdirectories after *.rar files. It should not match twice or more on the same rar volume. For example, blabla.part12.rar and blabla.part13.rar should now match twice.
[*]If exist verify the files against the included .sfv files that contains checksums of all rar files.
[*]Extract the rar volume into the same directory.
[*]If successfully extracted the files from the volume, delete the rar files.
[/list]

**Does it exist a tool for Linux/ubuntu that can do what [Par-N-Rar]("http://www.milow.net/public/projects/parnrar.html") can do for Windows?** Gui is not important.



**Alternative flow**
[list=1]
[*]Find all *.sfv files in specified directory/subdirectories.
[*]verify rar files against the checksum in the .sfv file.
[*]If OK, get a filename from the .sfv and send it to unrar
[*]unrar the volume
[*]Check if unrar has exited with CRC errors or someting else. If not, delete the rar files using the filenames found in .sfv file.
[/list]

---

### Post by emarkd on 2008-02-06
I don't know of an all-in-one like this for Linux.  You can always use the command line tools and write your own script :)

If you're getting these files from usenet, I'll throw out a recommendation for SABnzbd.  It handles these tasks automatically after downloading.  If that's not what you're doing, I withdraw my advice.

---

### Post by Blinkiz on 2008-02-06
> **Blinkiz said:**
> 
**Alternative flow**

[LIST=1]
[*][FONT="Fixedsys"]find /mydirectory -iname '*.sfv' -execdir cksfv -f {} \;[/FONT]
[*]Check exit code from cksfv: [FONT="Fixedsys"]echo $?[/FONT]
[*]If exit code is zero, grab first filename match (only one match) from the .sfv file that has .rar extension. **How?** I guess i do a [FONT="Fixedsys"]cat[/FONT] on the sfv file and pipe that to [FONT="Fixedsys"]sed[/FONT] and then pipe that to [FONT="Fixedsys"]grep .rar -m 1[/FONT]
[*]Unrar the grabbed rar file: [FONT="Fixedsys"]unrar e $filename.rar[/FONT]
[*]Check exit code from unrar: [FONT="Fixedsys"]echo $?[/FONT]
[*]If exit code zero, grab all filenames that has .rar extention found in .sfv file and delete them.** How?** I guess i do a [FONT="Fixedsys"]cat[/FONT] on the sfv file and pipe that to [FONT="Fixedsys"]sed[/FONT] and save the output in a variable and run[FONT="Fixedsys"] rm $variable[/FONT]
[/LIST]

**Please help me**

---

### Post by kwacka on 2008-02-06
Is gpar2 of any use to you?  (its in the universe repository).

---

### Post by nikoPSK on 2008-02-06
unrar maybe?

---

