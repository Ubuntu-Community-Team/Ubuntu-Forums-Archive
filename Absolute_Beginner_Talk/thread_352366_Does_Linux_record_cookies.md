---
title: "Does Linux record cookies?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by homh on 2007-02-03
When I used windows, it was of course always putting cookies onto my computer, especially those ad-tracking cookies.  Does Linux do the same?  If I put a file on my linux partion and then later delete it, is it recoveable?  I read all the time about police seizing computers belonging to suspects and recovering information from their computer that had been deleted.  Is the same thing possible with Linux?  I was just curious about how those things worked.

---

### Post by pseudonym on 2007-02-03
> **homh said:**
> When I used windows, it was of course always putting cookies onto my computer, especially those ad-tracking cookies.  Does Linux do the same?  If I put a file on my linux partion and then later delete it, is it recoveable?  I read all the time about police seizing computers belonging to suspects and recovering information from their computer that had been deleted.  Is the same thing possible with Linux?  I was just curious about how those things worked.
You can set Firefox to not accept cookies but doing so tends to have a crippling effect on your browsing experience. In any case, that junk you're talking about is not a problem in Linux. I think many websites that might drop ad-trackers don't bother with you if they know you're running Linux, because their code won't run on this OS (but I'm just guessing here). All I know is I and probably everybody else here don't experience the problem you describe.

As for data recovery, there are tools you can use for secure deletion of data. Some of them come bundled on the very useful [System Rescue CD]("http://www.sysresccd.org/Main_Page"), which you should check out anyway. I don't think those tools will stymie government people with highly sophisticated equipment, however. But i have no experience or knowledge in this area.

---

### Post by bodhi.zazen on 2007-02-03
Yes, Firefox (and other browsers) will download cookies. The problem with tracking cookies does not seem to be as problematic, but I do not know for sure. There are ways around this including browsing anonymously and using other browsers.

As far as data, yes in Linux as in other OS there are methods of data protection.

Like you perhaps I am paranoid and when you mention : > police seizing computers belonging to suspects

Well, without further information I am not sure I want to say more then that ...

---

### Post by mikewhatever on 2007-02-03
I've disabled cookies in Firefox, and added the sites I need to exceptions. For example, to use google/yahoo search or email, add google.com and yahoo.com to exceptions. The same applies to most of the sites, where you need to log in. Ubuntu forums, however, do not require cookies, but then it can't remember you, and you need to log in again.
When data is deleted from HD, it is not physically removed, but rather the HD space is marked as free to write to. The data remains there as long as it is actually overwritten by other data. It seems to be the same for any OS, for reasons of efficiency. There are ways to recover partial data even from a physically destroyed HD. To prevent something like this, one needs to use software that overwrites the existing data with the random sequence of numbers.

---

### Post by szf on 2007-02-03
If you are security-conscious you may want to browse in a virtual machine where all changes to the "filesystem" only occur in-memory.

When you close the machine, the cookies go away.

---

### Post by xpod on 2007-02-03
> I read all the time about police seizing computers belonging to suspects and recovering information from their computer that had been deleted. Is the same thing possible with Linux? I was just curious about how those things worked.

If you aint doing nothing wrong then you aint got nothing to worry about eh.

Right....wheres them cookies again:twisted:

---

### Post by jeremy on 2007-02-03
Just to be pedantic, it is not inux itself that stores cookies, rather it is the individual browser (firefox, opera, konqueror...). A far as I know, they can all be set not to accept cookies.

---

### Post by lamego on 2007-02-03
Or you can just use the LiveCD which is evern safer if you have tracking concerns...

---

### Post by C-A on 2007-02-03
I am surprised that there is not a firefox plug-in for secure data deletion of private information. I did a quick search and did not see one.

---

### Post by xpod on 2007-02-03
Tools>clear private data:)

---

### Post by C-A on 2007-02-03
> **xpod said:**
> Tools>clear private data:)

Cleared, but still there!

---

### Post by pseudonym on 2007-02-03
Restart Firefox and they should be gone.

---

### Post by albert006 on 2007-02-03
You can easily configure Firefox to remember cookies and other sensitive data only until you close it. Go to **Edit > Preferences > Privacy**.

If you only want to remove cookies when closing FF select **I close Firefox** next to **Keep Until:**

Do remove other private data, check **Always clear my private data when I close Firefox** and select the data you want to remove with the button **Settings**.

To remove private data when you are surfing click **Tools > Clear Private Data** or press Control+Shift+Del.

---

### Post by C-A on 2007-02-03
> **pseudonym said:**
> Restart Firefox and they should be gone.

It must be [ securely deleted]("http://en.wikipedia.org/wiki/File_wiping") to be gone.

---

### Post by xpod on 2007-02-03
> It must be  securely deleted to be gone.

For the ultra paranoind!
Of course never use geyes either if your having trouble with paranoia:)

---

### Post by aysiu on 2007-02-03
In your Firefox preferences, you can choose to have cookies cleared upon closing Firefox. You can also customize the settings for what's considered "private data" when you "clear private data."

---

### Post by liljoe76 on 2007-02-03
ctrl+shift+del
clear private data, built into ff

foxtor xpi for ff:
[http://cups.cs.cmu.edu/foxtor/](http://cups.cs.cmu.edu/foxtor/)

noscript xpi for ff, which _**all**_ should be using anyway....
[http://noscript.net/](http://noscript.net/)

and finally to disable third party cookies:
type **about:config** in address bar 
type **network.cookie.cookieBehavior**  in filter bar
change preference setting from 0 to 1

---

### Post by Maxwell7 on 2007-02-04
> **xpod said:**
> If you aint doing nothing wrong then you aint got nothing to worry about eh.

Well, I don't really agree with you on that. :) Even though I haven't got anything illegal on my pc (apart from the 5 mp3's i didn't buy myself) I still wouldn't feel happy or comfortable with anyone else going through my personal files. 

But I also belong to that category of people who don't like CCTV cameras all over the place. I like my personal freedom and privacy. That's very important for me. 

I plan to install a complete file system encryption within a couple months. I'm still working on my master thesis now, so I'm going to wait so that I won't screw anything up. 

I think file system encryption will stop most people from getting access to your files. Although that probably won't include people like the NSA. They can probably access  anything ;) But local police, and *especially* people who stole your laptop can't do anything with the information on the disk.

---

### Post by jrlii on 2007-02-04
Firefox can be set to "delete private data" when it is closed.

This will delete any cookies it may have accumulated during the session, along with the cache and history.

This may result in the cookies, history and cache being overwritten on a regular basis. I think it does, but that may depend on how the file system works. IIRC some file systems are set up to have a bias towards writing files where there are large un-fragmented stretches of disk space.

Deleted data: A "shredder" type utility which overwrites deleted data with random data before deleting it will stymie ordinary data recovery efforts like the police would use. However, preventing the the recovery of data by a really determined agency (like the NSA) which is willing to spend serious money to find out what was on a disk there isn't much short of reducing the drive to slag that will make sure the data isn't recovered.

---

### Post by lamego on 2007-02-04
> Well, I don't really agree with you on that. Even though I haven't got anything illegal on my pc (apart from the 5 mp3's i didn't buy myself) I still wouldn't feel happy or comfortable with anyone else going through my personal files.
Cookies have nothing to do with people accessing to your files...

---

