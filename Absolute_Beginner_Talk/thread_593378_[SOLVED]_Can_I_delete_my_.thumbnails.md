---
title: "[SOLVED] Can I delete my .thumbnails?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Hillerd on 2007-10-27
I found that .thumbnails in my home is occupying a huge amount of space.
Can I delete it? Most are from my picture collections but some are also Ubuntu themes.

---

### Post by Martje_001 on 2007-10-27
Yes, you can delete it. you can remove everything in your home-folder if you want..

---

### Post by por100pre1 on 2007-10-27
You can remove them but they will reappear after some time. To get rid of them for good, disable them in the **Preview** tab of Nautilus (the file browser) preferences.

---

### Post by Taxi on 2007-10-27
Eye of GNOME seems to save thumbnails there, too, when you open a file.  Other than looking around for and installing a better image viewer (which I'll get around to eventually) does anyone know a way to get EOG to cut that crap out?  I already set Nautilus to "never" show previews and I think it's EOG because when I tested it the only file that was thumbnailed was the actual file I opened, not any of the other files in the directory.

Thanks for any help and thanks to Hillerd for starting this thread, which reminded me how much it was bothering me.

---

### Post by Hillerd on 2007-10-27
Well thanks for the feedback. I deleted the directory, up to now without hick ups.
I do want previews in Nautilus, I find them quite handy when I am organizing my photos, so will have to live with it.
I once opened a thread on how to limit the .trash in size (sorry, I'm coming from WXP) and there were some nice scripts proposed to run regularly, which delete older files once a set limit is exceeded.
I will make one of those scripts for .thumbnails one day, in the meantime I'll have to do it manually. (I just start doing my first script, so it's not an easy job for me).

But anyway, I think that temporary files should be temporary, so deleted once they are not needed any more. Has anyone seen a filed issue on this?

While I am writing... The /tmp directory is purged from time to time. Somewhere I have seen the suggestion to make .thumbnails a link. So if I make it a link to /tmp/thumbnails, then this would be fine?

---

### Post by por100pre1 on 2007-10-27
> **Taxi said:**
> Eye of GNOME seems to save thumbnails there, too, when you open a file.  Other than looking around for and installing a better image viewer (which I'll get around to eventually) does anyone know a way to get EOG to cut that crap out?  I already set Nautilus to "never" show previews and I think it's EOG because when I tested it the only file that was thumbnailed was the actual file I opened, not any of the other files in the directory.

Thanks for any help and thanks to Hillerd for starting this thread, which reminded me how much it was bothering me.

Check if GQview does the trick:

```
sudo aptitude install gqview
```

---

### Post by Hillerd on 2007-10-30
In order to get rid of all the waste that is accumulating over time, I wrote a little script that limits the size of .Trash, .thumbnails and a cache used by worldwind. Here it is (my 2nd script in my life, so be careful, I am not 100% sure about what I am doing here):
```
#!/bin/bash
# clean trash from files older than today, if it holds more than <MaxMB> MBs
# reference: http://ubuntuforums.org/showthread.php?t=319211

MaxMB=95

# date: get current date
Currentdate=`date '+%F '`

for CleanWhat in ~/.Trash ~/.thumbnails ~/var/cache
do
#            loop while disk usage is > MaxMB
   while [ $(du -sm $CleanWhat |awk '{print $1}') -gt $MaxMB ]
   do
#            list files by modification date (descending), then get last (oldest) file 
      File=`ls -tad $CleanWhat/* |tail -1`
#            only files that are older than today
      if [ "`stat --format "%y" "$File"`" \< "$Currentdate" ]
      then
#            remove file
        rm -fvr "$File"
#            stop if there was an error
        if [ $? -gt 0 ] 
        then
          break
        fi
      else 
#            stop if the file is of today
        break
      fi
   done
done

exit
```

I am currently running it manually, but it could also be configured to run in certain frequencies (e.g. once a day, keyword "crontab").

---

