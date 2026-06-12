---
title: "Is there a program for finding duplicate files?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by psyguy92 on 2005-12-01
I'm wanting to check for dupilcate files, so I can remove the duplicates.  I'm mainly thinking of music files and images.  What options are available and what works well for you all?

---

### Post by earobinson on 2005-12-01
I did a google search for (dupilcate files linux) and found this [http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)

not sure if its in the ubuntu repos so i would search in synaptic (or apt-get) for (dupilcate files) and see what comes up, not on my linux box or i would do this myself.

let us know how it goes

---

### Post by YtiDilav on 2005-12-01
I also, always wanted this program.  I have contemplated writing the program myself and posting it free on the internet.  However, i can't quite figure out what the interface should be.  

I am not very motivated to write it however, because i have a workaround.  I share my Linux drive using Samba with my Windows machine.  In Windows i can use explorer and do a search by file extension (or all files), then sort by size.  For all files of identical size, i can check to see if it is the same file.  Then, delete the duplicates.

Although i can easily write a script or program to do this automatically.  How will the program know which file to delete?  And, sometimes i may want to keep both based on context.  ie. a directory of nice screen backgrounds, but also directory of vacation photos.  I can symlink the vacation photo in the backgrounds directory.  But i will probably delete the vacation photos after i write them to a DVD, then the symlink will be broken.  So, i prefer to keep two copies.

So, the question is, how can a program automatically clean up duplicates, and not accidentally delete files i want to keep even though they are duplicates?

---

### Post by aysiu on 2005-12-01
AmaroK can identify duplicate song files.

---

### Post by psyguy92 on 2005-12-01
[QUOTE=aysiu]AmaroK can identify duplicate song files.[/QUOTE]
Hadn't even thought of that. But, I don't think it can find 'exact' copies (same bitrate etc).  I think it just compares filenames/tags.  The thing that's nice about amaroK in this case is that you can right click and delete a found duplicate.

[QUOTE=YtiDilav]
So, the question is, how can a program automatically clean up duplicates, and not accidentally delete files i want to keep even though they are duplicates?[/QUOTE]
Hmm. I think with images, finding duplicates and letting the user click through the options one by one with preview thumbnails of each (with directory listing) would be great!

[QUOTE=earobinson]
I did a google search for (dupilcate files linux) and found this [http://www.pixelbeat.org/fslint/](http://www.pixelbeat.org/fslint/)

not sure if its in the ubuntu repos so i would search in synaptic (or apt-get) for (dupilcate files) and see what comes up, not on my linux box or i would do this myself.

let us know how it goes[/QUOTE]

I looked at synaptic and only found FDupe - it's command line, and that makes it really hard to deal with large numbers of files :(  
So I tried to get fslint (not in synaptic).  I got the tarball and it didn't extract correctly *boggle*.  So I got the .rpm and converted with alien.  That worked.  FSlint checks with sha1, and puts matches side by side. But you can't delete by right clicking.  

I guess I'll start with FSlint and navigate to the directories manually and delete one copy each, then for music, move to amaroK to find copies that aren't 'exact' (different bitrates etc).

Thanks for the pointers guys.  If anyone knows of an application that does all of this together, it'd be neat.  Otherwise, this works :)  Now I just have to find a good 8-12 hours to do it! :razz:

Edit: Oops, missed this.  In FSlint, you can select files by holding down ctrl and later clicking delete to kill em.  *opens eyes*

---

### Post by MartinG on 2005-12-01
Try KleanSweep.  It's a KDE tool, but if you get it from Klik you shouldn't have dependency problems even if you're a Gnome user (I'm on Kubuntu).

[http://klik.atekon.de/](http://klik.atekon.de/)

---

### Post by purpleturtle on 2005-12-01
I use a quick and dirty script containing the one liner:

find . -type f -print0 | xargs -0 md5sum | sort | uniq -w32 -d --all-repeated=separate | cut -c35-


This just prints out the duplicates - it doesn't attempt to delete anything automatically.

Hope this helps.

---

### Post by earobinson on 2005-12-02
[QUOTE=purpleturtle]I use a quick and dirty script containing the one liner:

find . -type f -print0 | xargs -0 md5sum | sort | uniq -w32 -d --all-repeated=separate | cut -c35-


This just prints out the duplicates - it doesn't attempt to delete anything automatically.

Hope this helps.[/QUOTE]
some would call that elegant, why dl and install a program to do a task when you can just pipe lots of small programs.

---

### Post by ChrisTheGeek on 2005-12-02
I agree, that is a very elegant solution.  

The problem I had was large number of similar or exact duplicate images in a complex folder structure.  I solved this by writing a shell script that took the directory to sort out, and the % similarity you wanted and it copied all matching pictures to a folder for you (renaming them to avoid conflicts).
 
Once you delete all the duplicates you no longer want, a second script moves and renames any files left back to their original location.

The script made use of this very funky debian package: [http://packages.debian.org/unstable/graphics/findimagedupes](http://packages.debian.org/unstable/graphics/findimagedupes)

For those with simpler needs, the built in Gnome thumnail viewer program in Applications->Graphics has the ability to find identical images recursively in a folder.  It only looks for 100% identical, but the UI is very good.

---

### Post by ranf on 2005-12-02
[QUOTE=psyguy92]I'm wanting to check for dupilcate files, so I can remove the duplicates.  I'm mainly thinking of music files and images.  What options are available and what works well for you all?[/QUOTE]
`gthumb' can do this for pictures.

---

### Post by sexcopter on 2006-01-09
I had a similar desire for such a program. Tried purpleturtle's one-liner and it worked with no probs. however also tried fdupes and it did it a hell of a lot faster. Both worthy solutions imo.

---

### Post by purpleturtle on 2006-02-16
I've improved my duplicate file finding "one liner" (just about) so that it is 1000's of times faster.. The obvious flaw with the original was that it was checksumming every single file to find the duplicates.  The easy optimisation is to only consider processing files which have the same size... 

# Check sizes first and only checksum files of the same size
find . ! -empty -type f -printf "%s '%p'\n" | sort -n | uniq -D -W 1 | \
  cut -d" "  -f2- | \
    xargs md5sum | sort | \
      uniq -w32 -d --all-repeated=separate | \
        cut -c35-

If anyone's interested here's each step of the pipeline explained:

# Prints out the size and filename of each file found on the path.
# and sort using the filesize as the key, then using uniq to 
# only leave filenames with the same size in the pipeline
find . ! -empty -type f -printf "%s '%p'\n" | sort -n | uniq -D -W 1 | \

# Trim off the file size in preparation for next stage
cut -d" "  -f2- | \

# Create the checksum for the files of the same size and then sort
xargs md5sum | sort | \

# Strip out any checksums that are unique, leaving only the duplicates
uniq -w32 -d --all-repeated=separate | \

# Strips out the checksum part, just leaving the duplicate filenames
cut -c35-

I've tried it a couple of times, and I think it works ;) 

You might want to give a size argument to the first find to only report files bigger than a certain size (e.g. 1 megabyte):

find . -size +1M -type f -printf "%s '%p'\n" .....


Hope someone finds it useful or maybe even interesting :)  .. I've really been getting into scripting with bash lately!

---

### Post by adamkane on 2006-03-06
These are all fast utilities that find all or almost all duplicates.

JUniq - Duplicate file remover:
JUniq generates a shell script with all the files to be deleted.
```

java -jar /<path to>/juniq.jar

``` [http://www.blisstonia.com/software/JUniq/]("http://www.blisstonia.com/software/JUniq/")

Unix shell script for removing duplicate files:
This script generates a second script with all the files to be deleted. It is the fastest method, but you are required to manually pick which files to delete, so it is actually the slowest method. It is probably a minor code change to pre-select all the duplicate files. This would also make a good Nautilus script!
[http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/]("http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/")

DupFinder.exe:
This utility gets the job done, if you can map a drive from an Ubuntu machine onto a Windows machine.
[http://support.microsoft.com/default.aspx?scid=%2Fdirectory%2Fworldwide%2Fen-gb%2Futility3.asp#XSLTSection126121121120]("http://support.microsoft.com/default.aspx?scid=%2Fdirectory%2Fworldwide%2Fen-gb%2Futility3.asp#XSLTSection126121121120")

---

### Post by Endolith on 2007-07-29
I think FSLint is the best option there is so far, but it's not that great.  :-/

In Windows, I use [Find Duplicates]("http://www.geocities.com/hirak_99/goodies/finddups.html").  It's better than FSLint because:

[LIST]
[*]you can delete all the dupes in a certain directory at once
[*]it warns you if you mark every instance of the file for deletion
[*]after you've deleted all but one instance of a particular file, it's removed from the list to let you focus on the others
[*]can delete directories that become empty
[*]you can use the delete key on the keyboard
[*]the interface is just better
[/LIST]

FSlint just shows you that the files are the same.  You still have to do all the work of deleting them.

---

### Post by Cannaregio on 2007-12-30
> **purpleturtle said:**
> I've improved my duplicate file finding "one liner" (just about) so that it is 1000's of times faster.. 


# Check sizes first and only checksum files of the same size
find . ! -empty -type f -printf "%s '%p'\n" | sort -n | uniq -D -W 1 | \
  cut -d" "  -f2- | \
    xargs md5sum | sort | \
      uniq -w32 -d --all-repeated=separate | \
        cut -c35-

Hope someone finds it useful or maybe even interesting :)  .. I've really been getting into scripting with bash lately!

Thanks a lot for the script.
Methinks that the ```
-W
``` switch should be lowercase, though: ```
-w
```

---

### Post by megamania on 2007-12-30
> **Cannaregio said:**
> Thanks a lot for the script.
Methinks that the ```
-W
``` switch should be lowercase, though: ```
-w
```
That's right, it should be lowercase.

This script has another problem, though: it doesn't work when it finds a filename containing a ' (an apostrophe).
I had noticed this before, but I'm honestly not able to fix this otherwise great script.

Can anybody please explain how to amend it?

---

### Post by syssyphus on 2008-01-01
> **megamania said:**
> That's right, it should be lowercase.

This script has another problem, though: it doesn't work when it finds a filename containing a ' (an apostrophe).
I had noticed this before, but I'm honestly not able to fix this otherwise great script.

Can anybody please explain how to amend it?


try this:

```
find . ! -empty -type f -printf "%s " -exec ls -dQ {} \; | sort -n | uniq -D -w 1 | cut -d" " -f2- | xargs md5sum | sort | uniq -w32 -d --all-repeated=separate | cut -c35-
```

---

### Post by megamania on 2008-01-02
> **syssyphus said:**
> try this:

I tested it and it looks like it works!

So the complete script should look like this:
```

find . ! -empty -type f -printf "%s " -exec ls -dQ {} \; | sort -n | uniq -D -w 1 | \
cut -d" " -f2- | \
xargs md5sum | sort | \
uniq -w32 -d --all-repeated=separate | \
cut -c35-

```

Thanks a lot!

---

