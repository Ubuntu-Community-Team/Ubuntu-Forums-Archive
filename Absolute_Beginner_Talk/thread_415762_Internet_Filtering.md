---
title: "Internet Filtering"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-04-20
I am pretty much converted to Ubuntu now. My kids like using Ubuntu too.  I would like to give them their own access.  I am holding back due to internet access for them, in XP I have filtering software which while being a pain in the backside for me most of the time I know they cannot access anything undesirable.  I have not seen any mention of any Linux applications that will limit access to undesirable sites for children.  Does anybody know of anything that would enable me to give the  anklebiters full unsupervised access to the internet in Linux?

---

### Post by steve.horsley on 2007-04-20
some references:
[http://www.linuxjournal.com/article/9044](http://www.linuxjournal.com/article/9044)
[http://software.newsforge.com/software/04/06/23/1521209.shtml](http://software.newsforge.com/software/04/06/23/1521209.shtml)
[http://www.google.co.uk/search?q=linux+web+content+filter](http://www.google.co.uk/search?q=linux+web+content+filter)

---

### Post by Campingman on 2007-04-20
> **steve.horsley said:**
> some references:
[http://www.linuxjournal.com/article/9044](http://www.linuxjournal.com/article/9044)
[http://software.newsforge.com/software/04/06/23/1521209.shtml](http://software.newsforge.com/software/04/06/23/1521209.shtml)
[http://www.google.co.uk/search?q=linux+web+content+filter](http://www.google.co.uk/search?q=linux+web+content+filter)

Thanks for that, I had googled and found the Dans guardian and squid links, it all looks mighty complicated to set up.  I will have a good read and give it a go.

---

### Post by Swab on 2007-04-20
Squid + SquidGuard is a lot of fun to setup!!  Expect to lose a lot of hair in the process!

---

### Post by Campingman on 2007-04-20
> **Swab said:**
> Squid + SquidGuard is a lot of fun to setup!!  Expect to lose a lot of hair in the process!

Just having a go with dansguard.  It is all going a bit pear shaped already!  If at first you don't succeed ........................:confused: :confused:

---

### Post by steve.horsley on 2007-04-21
What irritates me is athat I saw an article somewhere on an (apparently) easier filter package, but I can't remember the name or where I saw it. The package was specifically aimed at parents. I can't find it anywhere. But I can tell you that there are others besides dansguard.

---

### Post by Campingman on 2007-04-21
I am still at it. 
Tried Squid + Squidguard/ dansguard + squid/dansguard+tinyproxy/dansguard+tinyproxy+firehol
cannot get any of them to work on Feisty
Found this script which i thought would do the job
[http://ubuntuforums.org/search.php?searchid=18405556](http://ubuntuforums.org/search.php?searchid=18405556)
It just blocked all internet access.  I guess this may be just a bridge too far with my limited knowledge of Linux and networking.  I will perservere though.  Everything else in Feisty seems to be working ok so this can be my little project for the moment.

---

### Post by Campingman on 2007-04-21
I have just about given up.  There are no clear installation set up instructions that I can get to work for any of these applications, they either do nothing or completely block any internet access.  It is a shame as Ubuntu is great but with no parental control software XP will have to remain as the default for the children.  Does Edubuntu have filtering? Can you have Edubuntu dual booting with Ubuntu?
I will investigate Edubuntu further I think.

---

### Post by Hellcom on 2007-04-21
The wiki mentions a filtering system called willow, but I haven't tried any of these programs/filter sets due to my distinct lack of "ankle-bitters".

[https://wiki.ubuntu.com/ContentInternetFiltering/Willow](https://wiki.ubuntu.com/ContentInternetFiltering/Willow)

---

### Post by Campingman on 2007-04-21
Thanks for the reply hellcom,
I have tried willow too, Willow is a bit of a mystery the instructions are very sparse.  I placed it in a the directory as instructed /opt/willow and altered the conf file to the one advised.  But it would not run, the start instruction just came up with no such command, I have python installed?
I am just having another try with squid at the moment.

---

### Post by Campingman on 2007-04-21
Additional info for anybody searching for a filter:
Willowng is in synaptic and is a content filter, I could not get it to run in Feisty though
I finally found this thread
[http://ubuntuforums.org/showthread.php?t=232884&page=2&highlight=willowng](http://ubuntuforums.org/showthread.php?t=232884&page=2&highlight=willowng)
Which pointed me to somewhere I had not considered, Firefox addons, they have an addon called Procon Alba which filters out innaproprite content for the little people.  There is no password control and it is easily disabled but for young children it seems to be ideal.  It will do for my needs for a couple of years anyway (it will probably take me that long to figure out how to get dansguardian and squid working anyway).
[https://addons.mozilla.org/en-US/firefox/addon/1803](https://addons.mozilla.org/en-US/firefox/addon/1803)

---

### Post by Campingman on 2007-04-21
Just to finish off the information.  After playing with the procon add on it does have a password that can be set to make the add on invisible.  There are settings that can be altered to filter certain words, images and contant,  It seems to work perfectly.  I would recommend anybody looking for a content filter to have a look at this.

---

### Post by Swab on 2007-04-21
> **Campingman said:**
> Just to finish off the information.  After playing with the procon add on it does have a password that can be set to make the add on invisible.  There are settings that can be altered to filter certain words, images and contant,  It seems to work perfectly.  I would recommend anybody looking for a content filter to have a look at this.

Cool, glad you found something that works for you!

---

### Post by harpazo on 2007-04-25
I was able to get Dansguardian/Tinyproxy/Firehol to work with Feisty last night.  Follow the steps in both of these links and it will work great...
[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)
[http://ubuntuforums.org/showthread.php?p=2493322](http://ubuntuforums.org/showthread.php?p=2493322)

The find/replace of %q with %b in firehol from the second link was the key...

Harpazo

---

### Post by Campingman on 2007-04-26
Thanks harpazo,
I might give it a try again if the  procon addon fails to live up expectations

---

### Post by tatster on 2007-05-05
Campingman,

Are you trying to do filtering on the same machine that the little people use?

Tat.

---

### Post by irw on 2007-05-08
I used the script from the Ubuntu Chrsitian Edition to install their internet content filter based on Dans guardian - [link here]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html").  It comes with a useful GUI to change the settings

The script installed and set it up for me - and it worked fine.

I have just upgraded to Fiesty with a clean install, and aim to do this soon, as the children are now wanting access again.

---

### Post by Campingman on 2007-05-09
> **tatster said:**
> Campingman,

Are you trying to do filtering on the same machine that the little people use?

Tat.

I was trying to filter on the same machine yes

Thanks for that link irw, that looks like just what I need as it has a specific section for feisty.  To be honest at the moment the Firefox addon is doing a great job.  
When i get a couple of hours free i will give it a go.

---

### Post by Yaka on 2007-05-15
think i'll try that from christian edition as well now that i have no more hiar to pull out

---

