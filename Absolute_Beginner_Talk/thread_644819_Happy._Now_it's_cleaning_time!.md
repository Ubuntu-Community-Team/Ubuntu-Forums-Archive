---
title: "Happy. Now it's cleaning time!"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by anthonie on 2007-12-19
Hi all,

I am sorry if my question seems a little bit odd or, opposite, just plain stupid. 

The past few weeks I've spent some time installing everything that I want from my Ubuntu install. Of course there are things that I would like (mainly my ATI 9250 card to work, streaming vids from the net and that sort of stuff) but all in all I am happy to have a stable Gutsy install. 

I upgraded from Feisty and as a result I have an old kernel mentioned in my grub. Also, because I was experimenting with KDE (I use Gnome normally), I have a lot of KDE programs I don't use, and I would like to have them removed.

Where should I start to look if I want to clean up my system and remove anything I don't want, without actually breaking what I have?

As soon as I have my machine clean I can basically start optimising the system. At the moment, for instance, I have a very slow loading desktop (takes a good 20 seconds after session login).

Are there any general rules I should keep in mind? Any log files I should look into? I'd rather ask before I start playing around and breaking things I don't want to see broken.

Regards,

Anthonie

---

### Post by philinux on 2007-12-19
For the kde apps just remove them via synaptic.

---

### Post by chewearn on 2007-12-19
You can find a history of the installed packages in Synaptic, menu > file > history.

You can remove old kernels via synaptic as well, and the corresponding menu.lst entries should be deleted automatically.

---

### Post by anthonie on 2007-12-19
Thanks for the help. I installed most from the command line. For some reason I assumed I'd have to remove them command-line-style as well. Now I just removed about a gig of unwanted stuff and was able to remove the old kernel without any consequences much worse than Amarok starting as a first session and rebuilding my music-library. 

I've got some questions though.

ACPI as far as I know is meant for laptops, correct? I'd like to remove it but it threatens to remove Ubuntu Desktop as well than. I thought that to be somewhat drastic. However, I'd like to continue to remove as much as I can from Synaptic. Is there a way, I can undo what I uninstalled from the command line, just in case anything goes wrong and I can't get into GDM? And apart from reading the descriptions in Synaptic, trial and error, are there any other methods to determine what can go and what not?

As I mentioned in my first post, I have a very slow loading desktop. I assume Ubuntu stores information somewhere about the bootprocedure. What I'd like to find out is what exactly is causing the delay in order to eliminate it. However, I can't find that file. Is there anyone who could point me in the right direction? 

Is there a problem with Gutsy and streams or the latest kernel and streams? I had it up and running in Feisty, without ever having experienced problems. Now, the stream will open, play a second, and start buffering again, play a second, start buffering: ad infinitum. I have no firewall installed. File downloads go really fast. I installed Mplayer from source, installed all codecs (to my knowledge) and everything seems to work well, apart from the streams. Again, is there anyone who could give some pointers? 

Having read many horror stories on this forum about ATI, I suppose I should just stop thinking about installing a 256Mb 9250 AGP-card?

greetz and thanks for the time

anthonie

---

