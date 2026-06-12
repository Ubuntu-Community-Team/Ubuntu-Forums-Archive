---
title: "Issue with md5sum"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by ozzyzak on 2008-02-09
Greetings...

I've been away for a while but decided to come back and give Ubuntu another try.  One of the reasons this is so easy for me to do is because of all the great, helpful people on this forum.  So here is my issue:

I know how to generate md5s and I'm pretty sure I could even figure out how to create them and write them to a text file.  What I can NOT do however, is verify already existing md5s.

I've got tons of folders on an external drive, most with their own md5.  When I try to run md5sum -c nameofmd5, I get this:

scott@UBUN:~/Pink Floyd - 1971.10.17 New Mown Grass (PRS-CDR-008)$ md5sum -c 1971.10.17\ New\ Mown\ Grass\ \(PRS-CDR-008\).md5
: No such file or directory Grass_T101.flac
: FAILED open or readrass_T101.flac
: No such file or directory Grass_T102.flac
: FAILED open or readrass_T102.flac
: No such file or directory Grass_T103.flac
: FAILED open or readrass_T103.flac
: No such file or directory Grass_T104.flac
: FAILED open or readrass_T104.flac
: No such file or directory Grass_T201.flac
: FAILED open or readrass_T201.flac
: No such file or directory Grass_T202.flac
: FAILED open or readrass_T202.flac
: No such file or directory Grass_T203.flac
: FAILED open or readrass_T203.flac
md5sum: WARNING: 7 of 7 listed files could not be read
scott@UBUN:~/Pink Floyd - 1971.10.17 New Mown Grass (PRS-CDR-008)$ 

So apparently it can't find the files.  Is there some kind of limitation to the md5 program that I should know about?  All of those files are there, however one thing I note is it seems to be thinking the names are much shorter than they really are.  Or not, who knows...

Any ideas?

---

### Post by asmoore82 on 2008-02-09
could you post that md5sum file(it should be saved as plaintext)?
```
cat *.md5
```

---

### Post by ozzyzak on 2008-02-09
scott@UBUN:~/Pink Floyd - 1971.10.17 New Mown Grass (PRS-CDR-008)$ cat 1971.10.17\ New\ Mown\ Grass\ \(PRS-CDR-008\).md5
3b7ad4280b956106407128b893cde8d0 *1971-10-17_New Mown Grass_T101.flac
ce81125f3f1fe58f7515788981ac1b1d *1971-10-17_New Mown Grass_T102.flac
17c5ae2f26bdbccf9a7252085d6af5cf *1971-10-17_New Mown Grass_T103.flac
fcce8a4bd5d39e65eb7dff8cad1b4f19 *1971-10-17_New Mown Grass_T104.flac
0890aa29b23ad2e37bf29fa5e196c921 *1971-10-17_New Mown Grass_T201.flac
a0a772cb2e1156096b39d7b16a17e68c *1971-10-17_New Mown Grass_T202.flac
7a1e75e72fbb317f021914710dd31c49 *1971-10-17_New Mown Grass_T203.flac

---

### Post by asmoore82 on 2008-02-10
i think the `md5sum -c` method would work if you edited the md5 file and took out all the asterisks(*);
but it may be quicker and safer to just checksum the files again and compare the results...
```
cat *.md5
md5sum *.flac
```
-OR-
to be cute:
```
 cat *.md5 <( md5sum *.flac ) | sort
```

---

### Post by ozzyzak on 2008-02-10
I appreciate the help...but I have to wonder what happens when I pass these files along to someone with Windows XP.  They're going to have to put these asterisks back in I imagine.

Quite a hassle really....

thanks again!

---

### Post by kevdog on 2008-02-10
Could use a combination of grep, sed, cut, echo, etc to remove and then replace the astericks in the files.  It shouldn't be that hard to write a one line script!!

---

### Post by anemptygun on 2008-02-10
If you are a leet haxor, then no that wouldnt be hard at all ;)

---

### Post by ghostdog74 on 2008-02-10
```

find . -type f -exec md5sum {} \; | awk 'BEGIN{
 md[$1]=$2 
}
END{
 while ( (getline line < "file" ) > 0) {
    n=split( line, md5 , "*")
    if ( md[md5[1]] !~ md5[2]) {
     print "Not the same " md5[1],md5[2]
    }
    
 }
}'

```

---

### Post by anemptygun on 2008-02-10
great success :)

---

