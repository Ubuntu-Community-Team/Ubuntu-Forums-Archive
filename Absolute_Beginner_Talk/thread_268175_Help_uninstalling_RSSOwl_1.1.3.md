---
title: "Help uninstalling RSSOwl 1.1.3"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by seamus7 on 2006-09-29
I recently switched to Ubuntu. Love it! 

But after I installed RSSOwl using the Unofficial Ubuntu Dapper Guide: [RSSOwl installation instructions]("http://ubuntuguide.org/wiki/Dapper#How_to_install_RSS.2FRDF.2FAtom_Newsreader_.28RSSOwl.29"), I realized too late that I was installing an old version of RSSOwl and that, for whatever reason (something to do with Firefox or Java), it was consistently crashing. So, I want to uninstall RSSOwl.

My problem is that I can't find RSSOwl listed in Adept or Synaptic Package Manager even though it is listed in my Applications Menu. How do I do an uninstall in that case? Is there a simple way of uninstalling RSSOwl through a Terminal?

I also posted a thread on the [RSSOwl help forum]("http://sourceforge.net/forum/forum.php?thread_id=1582460&forum_id=296910") at SourceForge.net but the help I've gotten there isn't focusing on actually uninstalling RSSOwl. I'm hoping one of the many brilliant Ubuntu experts here can help! :KS

---

### Post by Kateikyoushi on 2006-09-29
I read the guide seems it installs only a few files manually.
RSSOwl is not in the repos that's why you can't find it in the package managers.

Delete the files you uncompressed from the tar file and created manually.

For example 

```
sudo rm -rf /opt/rssowl_linux_1_1_3_bin
sudo rm /usr/bin/runRSSOwl.sh
```

---

### Post by seamus7 on 2006-09-29
Okay. Thanks a lot for your help. I deleted those files.

Now, is there a way to remove RSSOwl from being listed in the Alacarte Menu Editor? And is there any danger in having remnants of RSSOwl that weren't uninstalled remain on my system? For instance, is there any way of removing dependency files that were installed with RSSOwl?

I'm bothered that RSSOwl didn't provide a clean way to uninstall their program. I don't get how that could happen. Am I missing something? Their program looks great and I might reinstall the newer version when I feel more confident with Ubuntu or RSSOwl gets included in a repository.

---

### Post by Kateikyoushi on 2006-09-29
Right click and edit menus then you can remove it.
Did it have any dependencies ? You just uncompressed a tar file and run it. 
I think the previous commands removed it entirely from your system even if not it wouldn't hurt your machine.

---

### Post by seamus7 on 2006-09-29
Oh ok thanks. 

At first, the right-click 'delete' option in Alacarte Menu Editor for the listing RSSOwl was inactive. I couldn't choose it. I then looked back at the Unofficial Ubuntu Dapper Guide and noticed that I would have created an RSSOwl.desktop file in the usr/share/applications/ folder. I deleted that file and went back to the Alacarte Menu Editor. The 'delete' option was now active. I chose it.

(I had just bought a second hard drive and reinstalled Ubuntu with a /home partition. I had been installing packages and doing a lot through the Terminal. By the time I had decided to install RSSOwl, my mind was a bit tired and I assumed everything would continue to install swimmingly. I failed to notice, as I said previously, that by following the Guide I was going to be installing an older version.)

---

### Post by freddybob on 2006-12-19
Thanks for posting these instructions, I had been trying everything to remove RSSOwl 1.1.3.

---

