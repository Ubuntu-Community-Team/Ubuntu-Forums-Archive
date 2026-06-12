---
title: "3 diff. kind of Problems/Questions"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-08
1) I finally configured my proftpd with a hell lot of fight...but in /etc/fstab where i am adding the mounted files whenever the file name consists of two or more words i fall into trouble like for eg.
> 
/Windows/H/Movies /home/ftp/Movies none bind  0  0

No problems with it ,but when i try to do
```

/Windows/H/English Movies  /home/ftp/Engli.....  none bind 0  0
```

and do ```
sudo mount -a
```

it says 
line -- in /etc/fstab is bad

Also is there any FTp Monitor available for proftpd

2) I need a software like winavi convertor to convert files to different formats especially  .vob format . AND also a DVD writing software.

3) All my drives are FAT 32 and i run a FTP server on my computer ...is it OK???
Or should i convert these to some other format and how do i do that?? because my GParted donot gives any option of converting.....

I have a dual boot system with Ubuntu 5.04 Hoary & Windows XP 

Kindly help me  [-o< [-o< [-o< ...... i have already fought enough in configuring Proftpd  ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by kombipom on 2006-03-08
I may be able to help with the first one:

When reading the fstab Linux thinks that the  "/Windows/H/English" and "Movies" are two items in a list as any whitespace is a list seperator.  You can usually either put the whole item in double quotes ie "/Windows/H/English Movies" to show that it is all one item or tell Linux that the space is just a space in the text (not a delimiter) by putting a backslash before it; ie /Windows/H/English\ Movies.  The second may be better in this case but give both a go and see which one works.

Note for pedants: 
I know that I am personifying Linux and that it doesn't "think" and that it is some process or other that reads the contents of /etc/fstab not "Linux" but you know what I am getting at.

---

### Post by Jucato on 2006-03-08
I think I only have answers for #1 and #3

1. Try using a "\" before the space, meaning it would be like this:
```
/Windows/H/English\ Movies  /home/ftp/Engli.....  none bind 0  0
```

3. Well, basically the main Linux partition should be ext3 or reiser, and the /home partition should always be non-FAT32 or NTFS. any drive that you will want to be seen in both windows and linux should be FAT32. That's far as I know.

---

### Post by animesh on 2006-03-08
Regarding qus 1 i tried both the ways......but it isn't working either way... :(

my /etc/fstab is pasted below

 ```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /Windows/C	vfat	iocharset=utf8,umask=000		
0       0
/dev/hda5       /Windows/D	vfat	iocharset=utf8,umask=000
0	0
/dev/hda6	/Windows/E	vfat
iocharset=utf8,umask=000
0	0
/dev/hda8       /Windows/G	vfat
iocharset=utf8,umask=000
0	0
/dev/hdb5 	/Windows/H	vfat	iocharset=utf8,umask=000	
0	0
/dev/hdb6 	/Windows/J	vfat	iocharset=utf8,umask=000	
0	0
/Windows/H/Movies /home/ftp/Junta/Movies none bind	
0	0
/Windows/H/Documentaries /home/ftp/Junta/Documentaries none bind 
0	0
"/Windows/H/Uploaded_movie_stuff...not_moved_yet"  /home/ftp/Junta/Uploaded_Movie_or_Documentary_not_moved_yet none  bind  
0	0
/Windows/J/Movies-5 /home/ftp/Junta/Movies-5 none bind
0	0
/Windows/J/TV_Serials /home/ftp/Junta/TV_Serials none bind
0	0
/Windows/J/Uploaded_TV_stuff...not_moved_yet  /home/ftp/Junta/Uploaded_TV_Stuff_not_moved_yet none bind
0	0
/Windows/G/Movies-6 /home/ftp/Junta/Movies-6 none bind
0	0
"/Windows/G/TV serials-2"  /home/ftp/Junta/TV_Serials-2  none  bind 
0	0
"/Windows/G/Uploaded misc. stuff...not moved yet"  /home/ftp/Junta/Uploaded_misc_stuff  none  bind
0	0
/Windows/E/Documentaries-2 /home/ftp/Junta/Documentaries-2  none bind 
0	0
/Windows/E/movies-2 /home/ftp/Junta/Movies-2 none bind
0	0
/Windows/E/Games /home/ftp/Junta/Games none bind
0	0
/Windows/E/videos /home/ftp/Junta/Videos none bind
0	0
/Windows/D/Movies-4 /home/ftp/Junta/Movies-4 none bind
0	0
/Windows/D/Music /home/ftp/Junta/Music none bind 
0	0
/Windows/C/acads/sem /home/ftp/Junta/Acads none bind
0	0
/Windows/C/Movies-3 /home/ftp/Junta/Movies-3 none bind
0	0
"/Windows/C/Pics,misc stuff" /home/ftp/Junta/Misc_stuff none bind 0	0

"/Windows/C/movied/installation files" /home/ftp/Junta/Installation_Files none bind
0	0
```

and when i do sudo mount -a i get

[mntent]: line 35 in /etc/fstab is bad
[mntent]: line 37 in /etc/fstab is bad
[mntent]: line 55 in /etc/fstab is bad
[mntent]: line 57 in /etc/fstab is bad
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point  does not exist
mount: mount point 0 does not exist
mount: mount point  does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: special device "/Windows/H/Uploaded_movie_stuff...not_moved_yet" does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist
mount: mount point 0 does not exist


and regarding qus 3 i was asking wrt speed .....

---

### Post by kombipom on 2006-03-10
I think that the > mount point 0 does not exist is because your entries are on more than 1 line and some of the lines now start with 0.  Each entry must be on a single line.  If they are all really on one line and it's just the way it shows up on the forum then I'll shut up and go away.

---

### Post by animesh on 2006-03-11
1) Thanks very much for your suggestion ,i have done that but some of my dir names are too large to be put in line..so how do i do that???

2) giving only the relevant portion of my /etc/fstab

```
[B]"/Windows/G/TV serials-2"  /home/ftp/Junta/TV_Serials-2  none  bind   0	     0

"/Windows/C/Pics,misc stuff"  /home/ftp/Junta/Misc_stuff  none  bind   0	 0

"/Windows/C/movied/installation files"  /home/ftp/Junta/Installation_Files  none  bind  0  0[/B]
```

on doing sudo mount -a

it gives bad format for all these lines which have quotes in them

---

### Post by zoehair on 2006-06-15
please help
i am try to get proftpd to run on a ubuntu 5.04 server, but it does not want  to work. is there know idionts guide for me(very new beginner) to help.

---

### Post by auberginepop on 2006-06-15
Guide to proftp. Worked for me on Breezy

[http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd+install](http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd+install)

---

