---
title: "Shell Scripting Help - Finding Files"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by root@localhost on 2007-10-17
I am working on writing a script to find all folders that contain images, and list the number of images contained in the folder. However, I'm not sure exactly how to go about doing this. I've worked out an appropriate find command, but I don't know what to do next, or if it's even possible to do this. In Java, it would be easy to throw the folders onto a stack and check to see if the folder was already there, but I need to keep this in Bash since I may need to actually execute it on the Windows PC instead of using a live CD. 

find /mnt/hda1/ -name "*.jpg" -print

Basically, the problem is that I need to find some lost images on a Windows PC. I was going to mount the drive from the Ubuntu LiveCD and run this command to find all folders with images, then narrow it down to the appropriate folder. 

Thanks!

---

### Post by teeceegee on 2007-10-17
Hello,

I'm not at home and not a bash scripter so I'm not able to test this out properly for you, but here's how I would tackle this in korn shell (I've tested it in Solaris as I'm at work and so unable to test in Ubuntu but it may give you some pointers):

for DIR in $(find /mnt/hda1/ -type d -print)
do
    JPGS=$(ls $DIR/*.jpg 2>/dev/null | wc -l)
    echo $JPGS $DIR
done | sort -n

This will print a list of the directories found in ascending order of the number of jpgs found in each one.

Hope this is useful

TCG.

---

### Post by Brucevdk on 2007-10-17
I'm not very good at this, but teeceegee just inspired me. Here's a one liner, little bit faster than teeceegee's because it doesn't go through each and every directory.

```

find / -iname "*.jpg" 2>/dev/null | sed "s/\(.*\)\/.*/\1/" | uniq -c | sort -n

```

You could add the different kind of extensions or use the *file* command to actually determine if a file is really an image (no matter what the extension). The latter most likely being a little bit more intensive.

Here's find with the -regex switch:
```

find ~ -regex ".*\(\.jpg\|\.gif\)" 2>/dev/null | sed "s/\(.*\)\/.*/\1/" | uniq -c | sort -n

```

---

### Post by teeceegee on 2007-10-17
Yes, that's much neater. I always forget about the uniq command.

---

### Post by root@localhost on 2007-10-17
Thanks for the replies! Would you mind explaining exactly what "2>/dev/null" means? I think I understand the rest of the first example, though the sed command has always been a little confusing to me since I've never really mastered regular expressions.   

As I understand it, the find command finds all the complete filenames, the sed command cuts out the filename from the end of each line, the uniq command eliminates duplicate folders, counting the number of occurrences, and the sort command does exactly what it sounds like. Is this correct? Also, does the sed command work with with filenames that contain extra dots? (such as "My Case Insensitive.Windows.Filename.jpg") 

Thanks!

---

### Post by teeceegee on 2007-10-17
2>/dev/null just means if there are any error messages, such as file not found, throw these away by sending them to the null device. If you want to see the effect of not having this there, in my example for instance, then just leave it out. You will see that for every directory that does not have any jpg files in it an error message gets written to the screen.

You can also redirect standard output using > instead of 2> (> is the same as 1>). You can send both standard output and standard error to the same file like this, for example:

ls *.jpg > filelist 2>&1

which tells the shell that 2> output should go where you've send 1> output.

TCG

---

### Post by Brucevdk on 2007-10-17
> **root@localhost said:**
> Thanks for the replies! Would you mind explaining exactly what "2>/dev/null" means?

TCG did an excellent job explaining this one, in my case there would have been a lot of *Permission Denied* errors which now miraculously disappear into the bit bucket.

> **root@localhost said:**
> I think I understand the rest of the first example, though the sed command has always been a little confusing to me since I've never really mastered regular expressions.

The regular expression in this case is: \(.*\/\).*

It contains a whole bunch of escaped characters, such as the parenthesis and the forward flash. The escaped parenthesis have a special meaning, the escaped slash is just there because the sed command itself uses forward slashes among other things to determine where an expression starts and ends.

[LIST]
[*]\($expression\) = capture an expression (so you can refer to it with variables \1 etc.)
[*].* = match any character (.) zero or multiple times, might have been wiser to use .+ (match any character at least once) but oh well.
[/LIST]

So in this case we capture the complete directory path, and cut the filename out. There's another command which uses delimiters and might be more appropriate in this case but I can't remember it.

```

/home/bruce/Pictures/photoforum185847296.jpg
|-------------------|
       matches

```

> **root@localhost said:**
> As I understand it, the find command finds all the complete filenames, the sed command cuts out the filename from the end of each line, the uniq command eliminates duplicate folders, counting the number of occurrences, and the sort command does exactly what it sounds like. Is this correct?

Yup you got it.

> **root@localhost said:**
> Also, does the sed command work with with filenames that contain extra dots? (such as "My Case Insensitive.Windows.Filename.jpg")

Yup works fine, we're not doing anything with the . character nor the filename itself really.

---

### Post by Brucevdk on 2007-10-17
> **root@localhost said:**
> I think I understand the rest of the first example, though the sed command has always been a little confusing to me since I've never really mastered regular expressions. 

I personally thought [Mastering Regular Expressions]("http://www.oreilly.com/catalog/regex/") (the Owl book) was a good book. Also *kregexpeditor* is a very nice tool to visually examine regular expressions.

---

### Post by root@localhost on 2007-10-17
Once again, thanks for the script. I'll be sure to check out that regular expressions book, but I think that a visual program like kregexpeditor might be easier for me to use. They make sense in theory, but I always have trouble when I sit down to write them. 

Anyways, I'm not sure if this is out of the scope of the Ubuntu forum, since I won't be able to execute this on a Linux box. I'm having a few problems with cygwin on the Windows machine. I can execute the program perfectly, but I can't figure out how to neatly package the script with cygwin so that the end user can run it without installing cygwin first. I don't need a full emulated environment--just a simple bash emulator to run this command. I'll be messing around with various ideas tonight, but I'd appreciate any insight on this issue. (If I figure it out, I'll be sure to post back here so others can learn how to do this.) I think the answer lies in packaging cygwin for a USB key or (preferably) a CD. 

Thanks again, 

root

---

