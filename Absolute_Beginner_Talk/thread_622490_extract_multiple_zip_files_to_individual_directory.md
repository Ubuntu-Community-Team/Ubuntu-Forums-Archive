---
title: "extract multiple zip files to individual directorys??"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-11-24
i have a directory full of zip files i would like to extract to their own seperate directorys.

i would like to be able to select all and right click and select "extract to seperate archive"


if not, cli will do.

out of interest if i had a directory that was full of sub directorys can i do the opposite and highlight all directoys and right clicks "archive to seperate zip" or the likes???

---

### Post by Danikar on 2007-11-24
You could probably do it with a perl script

Here is something below that might work.  Test it with like 3 or 4 zip files first.

Replace ~/ with the directory where your zip files are located.

Make sure that only zip files are in the directory when you try this.

```

#!/usr/bin/perl

$dir = '/home/danikar/zipfiles/'; #Your Directory
chdir $dir;

foreach (split /\n/, `ls -1`)
{
	/(.*)\.zip$/;
	`mkdir $1`;
	`unzip $_ -d $1`;
}

```

---

### Post by stinger30au on 2007-11-24
thanks , i also found 

[http://ubuntuforums.org/showthread.php?t=248354](http://ubuntuforums.org/showthread.php?t=248354)

hopefully it will work for .zip files as well

---

### Post by stinger30au on 2007-11-24
i have also found this one too

[http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/](http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/)

A. Linux or UNIX unzip command will list, test, or extract files from a ZIP archive, commonly found on MS-DOS systems.

When you want to unzip file using wild card, you have two options as follows.
Option # 1 : unzip multiple files using single quote (short version)

Type the command as follows:
$ unzip ‘*.zip’

Note that *.zip word is put in between two single quote, so that shell will not recognize it as a wild card character.
Option # 2 : unzip multiple files using shell for loop (long version)

You can also use for loop as follows:
$ for z in *.zip; do unzip $z; done

---

### Post by Danikar on 2007-11-24
I updated my code, it is tested.

just copy it into a text document.

Name it what u want, ill call it zip.pl

They use the script like this

perl zip.pl

---

### Post by Danikar on 2007-11-24
> **stinger30au said:**
> i have also found this one too

[http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/](http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/)

A. Linux or UNIX unzip command will list, test, or extract files from a ZIP archive, commonly found on MS-DOS systems.

When you want to unzip file using wild card, you have two options as follows.
Option # 1 : unzip multiple files using single quote (short version)

Type the command as follows:
$ unzip &#8216;*.zip&#8217;

Note that *.zip word is put in between two single quote, so that shell will not recognize it as a wild card character.
Option # 2 : unzip multiple files using shell for loop (long version)

You can also use for loop as follows:
$ for z in *.zip; do unzip $z; done


That wont put them in individual directories though. Though im sure you could do somthing similar.

Always could, 
```
perl -e 'foreach(split /\n/,`ls -1`){$_ =~ /(\S*)\.zip$/;`mkdir $1`;`unzip $_ -d $1`;}'
```

One liners heh =)

---

### Post by stinger30au on 2007-11-25
thanks for the feedback guys. i will test it shortly.

i am still trying to pack up my house, move in a few days. trying to fit in some ubuntu forum time when i need a break

---

### Post by stinger30au on 2007-11-25
> **Danikar said:**
> I updated my code, it is tested.

just copy it into a text document.

Name it what u want, ill call it zip.pl

They use the script like this

perl zip.pl



yee-haw!!!

works a treat!!!
thanks so much.

out of interest is it possible to do the reverse. have a ton of sub directory's and create individual zip files with the name of the zip files to be the directory name

example

test 1 (directory)
test 2 (directory)
test 3 (directory)

gives output 

test1.zip
test2.zip
test3.zip

---

