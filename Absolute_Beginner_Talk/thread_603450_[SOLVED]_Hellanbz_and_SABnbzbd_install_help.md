---
title: "[SOLVED] Hellanbz and SABnbzbd install help"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-11-05
Greetings all,
I downloaded two shell files for hellanbz and SABnbzbd, and actually figured out how to install them.  My question is how do I get them to work.  From reading around the forums, I am suppose to drop the nbz file into a folder, and hellanbz should start right up and go, but I can't figure out where this folder is.  And I have no idea how to tell if SABnbzbd is up and running and what to do with it.  Any help would be greatly appreciated.
Thanks!

---

### Post by felicity on 2007-11-05
I haven't used SABnzbd but to configure hellanzb you need to edit the /etc/hellanzb.conf file.

---

### Post by mangurt on 2007-11-05
I've configured that file, I guess I don't know how to run it (do I type hellanbz in terminal) or does it start up as soon as I download a NBZ file?
Thanks again

---

### Post by felicity on 2007-11-05
You can run it from a terminal by typing hellanzb, or if you want it to continually monitor the folder in the background you can add hellanzb to your System > Preferences > Sessions menu to begin on startup.

---

### Post by mangurt on 2007-11-05
Cool!  I will have to try this when I get home.  From what I've read, it's like the next best thing to buttered bread (when it comes to newsgroups):popcorn:

---

### Post by felicity on 2007-11-05
It's definitely cool if you have a source for nzb's (like nzbmatrix.com), and most posted on usenet usually have nzb's attached anyway. It's also nice to download to one folder and move to a completed folder when it's finished downloading. And you can also get a conky script if you want to easily keep up with what's being downloaded and how long you have left.

---

### Post by mangurt on 2007-11-05
I grab my nbz source files from binsearch.info  Love the site.  Will hellanbz work with this?
Thanks again

---

### Post by felicity on 2007-11-05
Yup, it will work with any site you can download nzb or zipped nzb's from.

---

### Post by mangurt on 2007-11-05
Ok, I am on my system at home, and tried starting hellanbz in terminal, and got 

bash: hellanbz: command not found

Now what?

---

### Post by felicity on 2007-11-05
Well it's hellanzb not hellanbz, that may be your problem!

---

### Post by mangurt on 2007-11-05
Ok, good call on my non-typing fingers....I think I am getting closer....

Now the error I get is 

ed@ed-desktop:~$ hellanzb
Could not find configuration file in the following dirs: ['/usr/etc', '/home/ed/etc', '/home/ed']
ed@ed-desktop:~$ 


Any other idea?

---

### Post by felicity on 2007-11-05
Are you sure the /etc/hellanzb.conf file is spelled correctly?  I've not seen that specific error myself. Did you install hellanzb from the repositories?

---

### Post by mangurt on 2007-11-05
I got hellanbz from a shell from this forum and ran it from there...

Hmmmm

---

### Post by felicity on 2007-11-06
You may want to try uninstalling it and then installing it from a terminal with:

```
sudo apt-get install hellanzb
```

---

### Post by mangurt on 2007-11-06
Ok, sweet, I got somewhere doing that.  Now all I have to do is figure out where the "queue" folder is, and how to put nzb files there...

---

### Post by felicity on 2007-11-06
You just edit the /etc/hellanzb.conf file. The section you want to edit to change the queue folder is:
```
# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = '~/edit/this/path'
```

you may also want to change this part to put your finished downloads somewhere you can find them easily:
```
# Where the fully processed archives go
Hellanzb.DEST_DIR = '~/edit/this/path'
```

---

### Post by mangurt on 2007-11-06
Hmm...ok, I changed those two lines (I have it set up for my queue folder to be my desktop) and the completed files to go to my videos folder.  I started hellanzb, and then downloaded a nzb file, but I don't see anything happening....am I suppose to see something going on in terminal?

---

### Post by felicity on 2007-11-06
If you started hellanzb in the terminal you should see it start up and say it's monitoring queue. Then once it begins a download you will be able to tell easily. If you have a downloaded nzb file in the queue folder, but hellanzb still just says 'now monitoring queue' that could mean your hellanzb.conf file isn't set to the right queue folder or something. Post that section of /etc/hellanzb.conf here if you want me to verify it.

---

### Post by mangurt on 2007-11-06
I really appreciate the help, I think I am so close it's not even funny


# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = '~/ed/Desktop'

# Where the fully processed archives go
Hellanzb.DEST_DIR = '~/ed/Videos'


This is where I would like to have the queued folder and the processed archives to go to my Videos folder

Thanks again :)

---

### Post by felicity on 2007-11-06
OK, looks good to me. And your saying you put an nzb file on your desktop and hellanzb just says 'now monitoring queue' still?

---

### Post by mangurt on 2007-11-06
Pretty much so..
I would think I would see something different..

---

### Post by felicity on 2007-11-06
Oh, my bad. I see your problem. It's because ~/ = your home directory, so ~/ed is redundant. You should put this instead:


```

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = '~/Desktop'

# Where the fully processed archives go
Hellanzb.DEST_DIR = '~/Videos'

```

---

### Post by mangurt on 2007-11-06
Bingo!  We have a winner!!!

Thank you for all you help!!!!

---

### Post by felicity on 2007-11-06
No problem; Hellanzb takes some getting used to at first, especially in regards editing hellanzb.conf, but it's great once you learn it. Enjoy!

---

### Post by mangurt on 2007-11-06
Oh, I am enjoying it....wow, such a great program!!!

---

### Post by samoid on 2007-12-23
Hi, i was trying to install Sabnzbd using this [http://terminalnerd.blogspot.com/2007/11/installing-sabnzbd-on-ubuntu-gutsy.html](http://terminalnerd.blogspot.com/2007/11/installing-sabnzbd-on-ubuntu-gutsy.html)
i got up to the final configuration and when i put mv SABnzbd.ini.sample ~/.sajavascript:void(0)bnzbd.ini into the terminal i get bash: syntax error near unexpected token `('

thanks ahead of time for your help

---

