---
title: "Do I need virus software?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by CallMeDerek on 2007-02-06
I have been using PC's since CPM - only two weeks on Linux and I have a question....

I am running two flavors of Linux, Kubuntu and DSL (on a old thinkpad) - Love them both and saving some printer driver, video codec and video driver headaches i really like the speed and usability of this platform.

So to my question....

I am running behind a router on a shared network connection over a windows network.

Do i need firewall for my Linux desktops and do i need virus software? I do run some windows apps with wine...  have spam filtering on my email server (hosted)... but how 'safe' is Kubuntu - do i need virus software for email/system scans and if so what would be recommended?

thanks in advance...

---

### Post by lyceum on 2007-02-06
quick answer, no. 

But, take a look at this for more info...

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

The only thing I do not think is mentioned there, if you have a file with a virus on it on your machine, it may (and should) do nothing. But, if you move it to a machine with Windows, the virus will come to life. So if you move info from MS to Ubuntu and vise versa, you may want to check it first.

---

### Post by matt_risi on 2007-02-06
I've been using Ubuntu for over a year now, and visit my share of.. shady websites, and I've never had a virus scanner running, and don't plan on it either.

---

### Post by mcduck on 2007-02-07
There's no need for antivirus/antispyware software, and as you are behind a router you shouldn't need any firewall either.

---

### Post by Steve Gates on 2007-02-07
The only reason is run AV would be if you read your emails on a Windows box as well. This way your Ubuntu box can safly receive and clean the emails, then you can clean them up before letting Windows see them

---

### Post by jd65pl on 2007-02-07
See this about virus' and anti-virus usage [http://co-project.lboro.ac.uk/users/cojd2/pages/l_virus.html](http://co-project.lboro.ac.uk/users/cojd2/pages/l_virus.html)

---

### Post by jvc26 on 2007-02-07
I'd only put AV on if you are exchanging files over your network/emails from ubuntu to windows as although you might not be able to be infected you can act as a host for the virus and it can be transferred.
Il

---

### Post by az on 2007-02-07
> **CallMeDerek said:**
> 

Do i need firewall for my Linux desktops and do i need virus software? I do run some windows apps with wine... 

Wine cannot make use of a windows virus.

And you don't need a firewall on a desktop system.  You always have the ability to know what's talking to the network and nothing is listening to the network by default (unless you install something that does).  Even if you were not behind a router, you do not need a firewall unless you are running some sort of server.

Just keep up-to-date with updates.

---

