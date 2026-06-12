---
title: "Mass audio conversion program??"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by timmins on 2007-01-31
HI, I am looking  for a program that will take all of my music files (MP3, ogg) and transcode them to level 5 ogg or 192 mp3 vbr bitrate files.  but I don't want a program that will trancode all of my files to .ogg.  I want the files to be in the same format though. Alsio I'm hoping there's a program that will leave files if they are at or below the desired level.

Does this exist?

---

### Post by Arisna on 2007-01-31
This sounds somewhat advanced.  You might consider scripting something involving sox, a command-line sound conversion utility.

---

### Post by timmins on 2007-01-31
> **Arisna said:**
> This sounds somewhat advanced.  You might consider scripting something involving sox, a command-line sound conversion utility.

what you said went right over my head, I'm a novice.


Ok, is there a program that will convert them all to ogg files, but leave the lower bitrate files where they are?

Thanks

---

### Post by IYY on 2007-01-31
The same answer in more novice-friendly terms: SOX is a utility that does the task you describe. However, it is not a graphical application but a command line tool. To install SOX, use the following terminal command:

```
sudo apt-get install sox
```

Once it's installed, you can learn about the command and how to using by issuing the following command:

```
man sox
```

Here is a very basic example of usage:

```
sox file.wav file.ogg
```

(the above will convert the wav file to ogg)

---

### Post by timmins on 2007-01-31
> **IYY said:**
> The same answer in more novice-friendly terms: SOX is a utility that does the task you describe. However, it is not a graphical application but a command line tool. To install SOX, use the following terminal command:

```
sudo apt-get install sox
```

Once it's installed, you can learn about the command and how to using by issuing the following command:

```
man sox
```

Here is a very basic example of usage:

```
sox file.wav file.ogg
```

(the above will convert the wav file to ogg)

Hey, I'm a torontonian too.

so, how would I convert all of my files on my UMS device "usbdisk" to level 5 ogg vbr,  and leave all of the files that are below that bitrate?

Thanks

---

### Post by timmins on 2007-01-31
to the top

---

### Post by IYY on 2007-02-01
I believe it only supports 128 kbps encoding for OGG; don't know if that's ok for you. If it is, you can use a script like this (assuming that /media/usbdisk is where the files are):

```

#!/bin/bash
cd /media/usbdisk
mkdir /tmp/oggfiles
for x in *.mp3
do 
sox "$x" /tmp/oggfiles/"`echo $x | cut -d'.' -f1`".ogg
done

```

this will take every MP3 file, and make a 128 kbps OGG file in /tmp/oggfiles. Note that this can take quite a long time. If 128 kbps doesn't cut it, you can convert to wav and then convert to ogg using oggenc. To only encode and copy the files over a certain bitrate, you can use the command mp3info (you can grab it from the repositories). 


```

#!/bin/bash
cd /media/usbdisk
mkdir /tmp/oggfiles
for x in *.mp3
do 
encoding=`mp3info -x "$x" | grep kbps | awk '{print $2}'`
if [ "$encoding" -lt "**128**" ]
then
echo "not copying"
else
sox "$x" /tmp/oggfiles/"`echo $x | cut -d'.' -f1`".ogg
fi
done

```

Now, if the 128 figure is not good enough for you and you would like to first encode to wav and then to ogg, you would use...

```

#!/bin/bash
cd /media/usbdisk
mkdir /tmp/oggfiles
for x in *.mp3
do 
encoding=`mp3info -x "$x" | grep kbps | awk '{print $2}'`
if [ "$encoding" -lt "**128**" ]
then
echo "not copying"
else
newname="`echo $x | cut -d'.' -f1`".wav
newdir="/tmp/oggfiles/"
sox "$x" "$newdir$newname"
oggenc --quality=**5** "$newdir$newname"
fi
done

```

I think these scripts should work. Of course, you can tweak them to use any values you like instead of the bolded values.

By the way, do you know about the Ubuntu Toronto group? We meet at the Linux Caffe every other Wednesday.

---

### Post by bahn on 2007-04-10
> **IYY said:**
> I believe it only supports 128 kbps encoding for OGG; don't know if that's ok for you. If it is, you can use a script like this (assuming that /media/usbdisk is where the files are):

```

#!/bin/bash
cd /media/usbdisk
mkdir /tmp/oggfiles
for x in *.mp3
do 
sox "$x" /tmp/oggfiles/"`echo $x | cut -d'.' -f1`".ogg
done

```

this will take every MP3 file, and make a 128 kbps OGG file in /tmp/oggfiles. Note that this can take quite a long time. If 128 kbps doesn't cut it, you can convert to wav and then convert to ogg using oggenc. To only encode and copy the files over a certain bitrate, you can use the command mp3info (you can grab it from the repositories). 


```

#!/bin/bash
cd /media/usbdisk
mkdir /tmp/oggfiles
for x in *.mp3
do 
encoding=`mp3info -x "$x" | grep kbps | awk '{print $2}'`
if [ "$encoding" -lt "**128**" ]
then
echo "not copying"
else
sox "$x" /tmp/oggfiles/"`echo $x | cut -d'.' -f1`".ogg
fi
done

```

Now, if the 128 figure is not good enough for you and you would like to first encode to wav and then to ogg, you would use...

```

#!/bin/bash
cd /media/usbdisk
mkdir /tmp/oggfiles
for x in *.mp3
do 
encoding=`mp3info -x "$x" | grep kbps | awk '{print $2}'`
if [ "$encoding" -lt "**128**" ]
then
echo "not copying"
else
newname="`echo $x | cut -d'.' -f1`".wav
newdir="/tmp/oggfiles/"
sox "$x" "$newdir$newname"
oggenc --quality=**5** "$newdir$newname"
fi
done

```

I think these scripts should work. Of course, you can tweak them to use any values you like instead of the bolded values.

By the way, do you know about the Ubuntu Toronto group? We meet at the Linux Caffe every other Wednesday.

Would this recursively look in sub directories for .mp3s?

---

