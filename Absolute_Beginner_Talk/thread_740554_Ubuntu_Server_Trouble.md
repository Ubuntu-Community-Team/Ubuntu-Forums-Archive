---
title: "Ubuntu Server Trouble"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by The Chewy Wun on 2008-03-30
I'll start this off by saying, I'm much more knowledgeable of Windows than Linux, but am trying to even things out a little bit.  I have a Dell PE 2800 fairly new (within last 3 years, 3.4 gig Xeon, 2 gigs Ram, Raid card, and 2 satas).  

I installed Ubuntu server 7.10 and seem to have everything configured correctly.  I'm able to go out to the internet and download tar.gz installation packages.  However, when trying to extract these files and install them, it just does not work. 

For instance I want to install a DUC client, and was able to create a download directory, use the wget command to download the tar, used tar xzf xxxxfilenamexxx.tar.gz and it errors out or just sits there and hangs up.  I installed all the optional software packages during the installation, thinking that that was the best way to go.  

Any ideas or thoughts?  Thanks in advance.

---

### Post by Tatty on 2008-03-30
Im far from an expert at compiling software,

But where does it "error out"?  can you post some error messages?

Also, what is the name of the software you are trying to install?  is it not in the repositories?

---

### Post by The Chewy Wun on 2008-03-31
Once or twice I've extracted the tar ok, and when running sudo make install I get an error.

Most of the time though, the extraction just hangs, I lose the prompt and hitting enter does nothing I have to hit control c to get back to a prompt.

So far, I've tried installing a no-ip duc client, webmin, and webcp, all of which I went to the internet to download the files for.  These are the 3 major things that I want running on this box for now.

---

### Post by Nythain on 2008-03-31
ok, to solve a lot of your compiling issues... you need build-essential
sudo apt-get install build-essential
that will install the packages necessary to compile most stuff from source...

as far as your tar experiences go, not sure if i can help much there, other than saying, make sure your syntax is correct, remember linux is very CaseSenSitiVe and doesnt like spaces in file names and paths to much without either ' ' around stuff or when the space is preceded with a \

also, im not sure, but tar probably has a v for verbose, wich can help a lot with figuring stuff out

wish i could help ya more on the tar but it works pretty darn well for me :(

---

### Post by The Chewy Wun on 2008-03-31
Thanks for the reply.
The build essential command got the duc client installed.

Next, I went to the webmin-dl folder where the tar was downloaded to and I tried these 3 combinations

[COLOR="Red"]tar xzf webcp-0.5.7.tar.gz[/COLOR]
      Gzip: Stdin: not in gzip format
      Tar: Child return status 1
      Tar: error exit delayed from previous errors

[COLOR="Red"]tar xzv webcp-0.5.7.tar.gz[/COLOR]
       Hangs

[COLOR="Red"]tar xz webcp-0.5.7.tar.gz[/COLOR]
       Hangs

I feel like I'm close, at least the install command worked for the duc client

---

### Post by Oldsoldier2003 on 2008-03-31
> **The Chewy Wun said:**
> Thanks for the reply.
The build essential command got the duc client installed.

Next, I went to the webmin-dl folder where the tar was downloaded to and I tried these 3 combinations

[COLOR="Red"]tar xzf webcp-0.5.7.tar.gz[/COLOR]
     ** Gzip: Stdin: not in gzip format**
      Tar: Child return status 1
      Tar: error exit delayed from previous errors

[COLOR="Red"]tar xzv webcp-0.5.7.tar.gz[/COLOR]
       Hangs

[COLOR="Red"]tar xz webcp-0.5.7.tar.gz[/COLOR]
       Hangs

I feel like I'm close, at least the install command worked for the duc client

try redownloading the tarball i've highlighted something that should send up red flags...

---

### Post by The Chewy Wun on 2008-03-31
I tried but keep getting the same errors on trying to extract it.

---

### Post by Iowan on 2008-03-31
Forgive me if I'm off base...
I thought **tar** options started with "-", so **tar -xzf webcp-0.5.7.tar.gz**

---

### Post by chilinski on 2008-03-31
> **Iowan said:**
> Forgive me if I'm off base...
I thought **tar** options started with "-", so **tar -xzf webcp-0.5.7.tar.gz**

The hyphen isn't required any more.

Chewy, are you trying to install webmin? If so, you can do it with an apt-get. However, it fails to install something the first time and you have to do an apt-get update, which fixes everything and lets webmin run. That's from memory...I did it twice and it was the same both times on Gutsy. But I can't remember it exactly.

---

