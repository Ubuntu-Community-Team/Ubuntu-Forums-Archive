---
title: "Wine - accessing generated files"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-07-08
I am using Crossover version of Wine to run certain windows aps.  If I accept default file storage locations, files created using these applications will be stored within their respective "bottles."  If I need to access these files using native Ubuntu applications, how is that possible?

For instance, I used DVDFab to back up a DVD disk to an ISO file.  If I allow, the program defaults to a storage location within the bottle.  Now, let's say I want to use VLC to play that ISO file.  How would I navigate to the file?  It doesn't seem possible to me.

Now, I know that I can direct DVDFab to store the generated ISO elsewhere - say onto my slave NTFS HD.  I have done that, but, the output is not good - don't know if that is the result of sending the results to a storage location outside the bottle or not - but would like to test the application by storing within the bottle - I just don't know how to access the bottle from other than within Wine.

The same would be true if I generated a text file from MS Word.  If I allow the system to select the storage location, the file will be saved to the 'my documents' folder within Wine.

The only way I've found to retrieve and work further with that file is to open up Word from within Wine.  The file is not detected by the native Ubuntu browser.

Suggestions would be welcome.

Thanks.

Caruso

---

### Post by ellgor on 2007-07-08
> **carusoswi said:**
> I am using Crossover version of Wine to run certain windows aps.  If I accept default file storage locations, files created using these applications will be stored within their respective "bottles."  If I need to access these files using native Ubuntu applications, how is that possible?

For instance, I used DVDFab to back up a DVD disk to an ISO file.  If I allow, the program defaults to a storage location within the bottle.  Now, let's say I want to use VLC to play that ISO file.  How would I navigate to the file?  It doesn't seem possible to me.

Now, I know that I can direct DVDFab to store the generated ISO elsewhere - say onto my slave NTFS HD.  I have done that, but, the output is not good - don't know if that is the result of sending the results to a storage location outside the bottle or not - but would like to test the application by storing within the bottle - I just don't know how to access the bottle from other than within Wine.

The same would be true if I generated a text file from MS Word.  If I allow the system to select the storage location, the file will be saved to the 'my documents' folder within Wine.

The only way I've found to retrieve and work further with that file is to open up Word from within Wine.  The file is not detected by the native Ubuntu browser.

Suggestions would be welcome.

Thanks.

Caruso
Hi,

 Not exactly what you say in your post, but, I found that I had trouble opening any file with VLC, tried evrything to no avail (except for myriad copies of 1 file) then I stumbled on Directories in the VLC and before I finished pressing the key the Directory was playing. So instead of looking for a particular file look for the directory instead ( you actually get a different screen to choose the directory) hope this is of help.

Regards, Ellgor.

---

### Post by carusoswi on 2007-07-10
> **ellgor said:**
> Hi,

 Not exactly what you say in your post, but, I found that I had trouble opening any file with VLC, tried evrything to no avail (except for myriad copies of 1 file) then I stumbled on Directories in the VLC and before I finished pressing the key the Directory was playing. So instead of looking for a particular file look for the directory instead ( you actually get a different screen to choose the directory) hope this is of help.

Regards, Ellgor.

Thanks for the reply, elgor.  I'm not certain if I understand you or not.  I am pretty comfortable at navigating through volumes, directories, etc.  My problem is this:

If I allow any application running in Wine to store to the default location, that location is always along what I suppose is a "virtual" directory - each ap in Wine has it's own Windows directory tree, and generally defaults to the 'my documents' folder in that tree.  To my knowledge, there is no way to access files stored there except that you open the application that created the file and navigate to the file through that application's 'open' command.  

I would be happy if you can tell me that I'm wrong and explain how, for instance, I might create a document in MS Word running in Wine, then, access that file and open it using Open Office running natively in Ubuntu.

. . . not that I would ever need to do that - but, if I create an ISO of one of my movie DVD's, I need to open it with VLC.

Generally, I store the ISO files on my Ubuntu desktop or an external NTFS hard disc.  If I create those ISO files using DVDFab running under XP, they play fine, either from XP or from Ubuntu (running VLC natively from either OS).  If I run DVDFab from Wine, the resulting file will not play properly.  It has all manner of artifacts.  I'm guessing that there may be some sort of real-time speed problem that is messing things up (but that's just a guess).

I'd like to try storing an ISO in the default Wine directory for DVDFab, but, I already know (or I am of the impression) that I will be unable to access the storage location from VLC.

I think you've tried to tell me that I can - but, I didn't quite get it.  Could you tell me again.

Thanks.

Caruso

---

