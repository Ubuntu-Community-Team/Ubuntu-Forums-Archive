---
title: "wanting to compress a folder consisting of html and jpgs (a mirrored website)"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-06-22
I've got a folder containing a mirrored website. It contains HTML pages and some jpegs. I'm going to be uploading them to a website for temporary storage, as i move from one pc to another, and from one place to another.
The folder is about 700mb big. When i did File Roller on it and chose tar.gz as the extension, the archive was  220 mb.


I don't think i can just save them to an external hard drive or burn them to a CD-rom.  So this is out of the question.

how do i compress a directory's contents (files and subdirectories) via commandline using Max compression? I'm willing to use the folder name as the folder name for the archive. i need to keep the directory structure.

What level of compression does GUI File roller do? I heard that FileRoller (archive manager) doesn't do max compression, and this is why I ask about compressing via cli. Is it possible to change the compression level of File Roller?


Is bzip as safe as gzip? i mean, no greater risk of file corruption, lost data etc? 
is doing a plain "tar" (archiving only)  safer than a tar and gz (archiving + compression)?

What about rzip? I learned about it only today at [http://jeremy.zawodny.com/blog/archives/001842.html](http://jeremy.zawodny.com/blog/archives/001842.html). It is the best in terms of both time and compression ratio. If it's good, how come, it's not installed by default on our ubuntu?

I installed rzip, and am trying to zip the folder named [www.website.com](www.website.com)  with the following command: "rzip -9 -k -P www.website.com"

I get the following error message:

Failed to map buffer in rzip_fd
Fatal error - exiting

what's wrong?

Also, should i bother with MD5 file to know whether there is a corruption of the file?

---

### Post by glotz on 2006-06-22
That's right about file roller compression level. You can set the level using the Configuration Editor (gconf-editor) (apps > file roller > general > compression level)

I would think that archiving would be safer than archiving and compressing.
EDIT: I think calculating a MD5sum is a good idea. It's fast and you'll know if there was a problem. On the other hand, the unzipping utility probably performs some CRC check that might do the job for you allready. (Might not uncompress if there are CRC errors)

---

### Post by hanzj on 2006-06-22
glotz,
thanks. i changed it from "normal" to "maximum". Does this affect both 'tar.gz" and "tar.bz2"?

---

### Post by glotz on 2006-06-22
You're welcome. I have no idea but that'd seem logical.

---

