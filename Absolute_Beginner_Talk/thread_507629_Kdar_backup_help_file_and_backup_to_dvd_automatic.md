---
title: "Kdar backup help file and backup to dvd automatic"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-23
[I have installed Kdar using this info and it will start up fine.]("http://ubuntuforums.org/showthread.php?t=500492&highlight=install+kdar+fiesty")

When the program runs and i click on the help button and click the "Kdar Handbook" botton so i can read the help file i get this error

Could not launch KDE Help centre - Could not find khelpcentre.

Where do i find this file to add so i can read it and learn more.


Also, when creating a profile if you go in to options there is a checkbox that says "pause between slices - command to run after writing each slice"
[URL="http://kdar.sourceforge.net/"]
i had a browse at the online documents here
[/URL]

and i read this about being able to burn the slices

    *

      Command to execute after completion of each slice": KDar can optionally run arbitrary shell commands after each slice has been written. Use this to run your DUC (Dar User Command) files, a CD burning program (k3b), or an secure-shell file transfer to a remote server. Include the full path to the script or binary file if it is not in your $PATH environment variable. Leave this command empty if you do not want to run any external programs.

      KDar can substitute the following DAR macros here:
          o

            %%: replaced by "%"
          o

            %p: the path to the archive slice
          o

            %b: the basename of the archive slice
          o

            %n: the number of the archive slice
          o

            %e: the extension of the archive slice (always "dar")
          o

            %c: the context in which the slice has been written or read

      For example, to start “k3b” with the archive slice loaded and ready to burn onto a CD, put the following in the command box:

      k3b --datacd %p/%b.%n.%e

      See the DAR manpage (man dar) for details on string substitution.


so can i just copy and paste this part "   k3b --datacd %p/%b.%n.%e" in to the config of kar and run it so that when kdar finishes makiing a slice of data (i would assume its an iso its building  to the hdd ) that this line will do the trick to make it burn every slice it creates.

if i want it to burn to a dvd instead of cd do i change it from
   k3b --datacd %p/%b.%n.%e
 
to

   k3b --datadvd %p/%b.%n.%e



Does it over write each slice it creates or does it make a new file for each slice it creates?

sorry to ask so many questions.
thanks for your time

---

### Post by weijie90 on 2007-07-23
> **stinger30au said:**
> [I have installed Kdar using this info and it will start up fine.]("http://ubuntuforums.org/showthread.php?t=500492&highlight=install+kdar+fiesty")

When the program runs and i click on the help button and click the "Kdar Handbook" botton so i can read the help file i get this error

Could not launch KDE Help centre - Could not find khelpcentre.

Where do i find this file to add so i can read it and learn more.


Try running "sudo aptitude install khelpcenter" in a terminal.

---

