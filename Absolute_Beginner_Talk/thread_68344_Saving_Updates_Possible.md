---
title: "Saving Updates Possible?"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by NZ-Wanderer on 2005-09-22
Is there a way to be able to save updates locally??

My reason for asking is that I seem to muck things up all the time there-by finding myself reinstalling Ubuntu a lot...
Now the updates are well over 300, it takes forever for me to download them (between 3-4 hours)...

What would be nice is if I could save the update files to a separate partition so when I reinstall the next time I can just copy them over to where-ever they belong...

Is this possible at all??

---

### Post by bsussman on 2005-09-22
try looking in /var/cache/apt/archives/

---

### Post by NZ-Wanderer on 2005-09-22
[QUOTE=bsussman]try looking in /var/cache/apt/archives/[/QUOTE]
 Thank you very much for that, I will copy the /archives folder over to another drive, and the next time I re-install I will be able to just copy it back :) :)

---

### Post by bsussman on 2005-09-22
look into apt-get clean and apt-get autoclean

since you are planning to re-archive, you may want to save space.  

OR

 I think it possible to have apt-get just put the files in another place.

OR

You could soft link  the var/cache/apt/archive to a place in another filesystem.

It is a unix rule that there should always be 8 ways to do something, when 1 will do...

---

### Post by NZ-Wanderer on 2005-09-23
Thanks again :) :)

I will try out that apt-get clean and apt-get autoclean to see what they do.. - I guess they might get rid of the junk I been installing and uninstalling..
Have already made one copy of the archives folder (all except for one file it wouldn't let me copy (lock) - so I will archive the folder again after I do the clean and see if there is any difference...

On another note, I don't suppose you would know if Kubuntu uses the same archive files as Ubuntu do you??

[COLOR=Red]UPDATE:[/COLOR] Ohh that clean or auto clean command is dangerous isn't it?? - I ran both commands and then went to look in my archive file.. - Imagine my suprise when I found the only thing left in the folder is the lock file.. - Everything else had disappeared... :(

---

### Post by bsussman on 2005-09-23
[QUOTE=NZ-Wanderer]Thanks again :) :)
[color=Red]UPDATE:[/color] Ohh that clean or auto clean command is dangerous isn't it?? - I ran both commands and then went to look in my archive file.. - Imagine my suprise when I found the only thing left in the folder is the lock file.. - Everything else had disappeared... :([/QUOTE]

Um - what part of 'look into' means 'trust bsussman?'

Re-read point 2 in my signature.

There is a significant amount of space taken up on your disk with documentation - some of it is understandable.

In this case the damage is slight - the repositories are very active, things are changing, what with the new release due shortly. You only lost some re-install convenience(time to re-download).

Anyhow, if things get really screwed up, you can invite me down to help you sort it. I wonder if that hot bath hole I dug is still there, over on the Coromandel side. :)

---

### Post by NZ-Wanderer on 2005-09-23
hehe well I have now re-installed twice more since I mucked up that clean part....

I did try to reinstall the backups I had made after one of the reinstalls, but for some reason my permissions are all screwed up.. - Before I could open a GZ file with "extract here" - now I get an "extract to" message and when I try to extract I get no permission..
Not sure what gone wrong, cause I have been good and not tried altering anything (apart from manually setting /, /swap, /home and /windows partitions when actually installing...) - I can't see tho why permissions would be altered just because I made partitions in the install instead of telling it to auto do everything.

** Looks around for hot bath hole but doesn't see one anywhere around Christchurch **

---

### Post by bsussman on 2005-09-24
[QUOTE=NZ-Wanderer]
 I can't see tho why permissions would be altered just because I made partitions in the install instead of telling it to auto do everything.[/QUOTE]
 
You are extracting your own hand made backup? into the archive directory? Did you use tar? tar has certain defined behaviors with regard to file ownership that may play in your problem, both on the way out and in to a TAR file. gzip too.
 
 I expect there is a mismatch tween permissions tween your id, the id when you TARed it up and the dir you are restoring to.
 
I assume we are still talking about apache and mysql? Apache and mysql both should be installing with ultimate owners that are neither root nor you - both have special users. This adds another twist.
 
 I hope I am not giving you too much data - it is difficult when we don't see all the details of all the actions all the time.

  >  ** Looks around for hot bath hole but doesn't see one anywhere around Christchurch **
 Mine should be right on the beach where I left it - deep one too - could fit at least two people:grin:

---

### Post by NZ-Wanderer on 2005-09-24
[QUOTE=bsussman]You are extracting your own hand made backup? into the archive directory? Did you use tar? tar has certain defined behaviors with regard to file ownership that may play in your problem, both on the way out and in to a TAR file. gzip too.[/QUOTE]

Umm I just used the "File Browser" then right clicked on a folder and went "create archive' - No matter tho, I got my favourite winblows file manager running under wine now, so I can use that to zip up any directory that I want :)

[QUOTE=bsussman]I assume we are still talking about apache and mysql? Apache and mysql both should be installing with ultimate owners that are neither root nor you - both have special users. This adds another twist.[/QUOTE]

We were talking about those things?? - geee, I don't even know what they are 

[QUOTE=bsussman]Mine should be right on the beach where I left it - deep one too - could fit at least two people:grin:[/QUOTE]

Ahh I remember seeing that hole.. - I heard that it got filled in when our Prime Minister got caught in it going over 120kph LOL (You have to live in NZ to appreciate that)

---

