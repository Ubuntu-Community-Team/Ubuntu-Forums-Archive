---
title: "feel like an idiot..."
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Lighthouse on 2006-08-31
OK, I feel like an idiot. I'm usually pretty computer savvy. i got ubu installed on an old laptop and i'm not too intimidated by the cmd line but damn...

first off, i have gimp 2.0 installed. i'm pretty good at using paint shop pro on windows--dealing w/ vectors, layers, et al. can't seem to find my way around the gimp. guess what? NO HELP is installed! 

So i come here looking for how to get it. GRRRRRRRR! i get no frickin' clue about what to do. i did a search and get something close but it's for dapper.

guess what? I don't know if i have dapper loaded. why? b/c i can't figure out how to find out what version i'm running. i loaded this thing months ago. 

I go into the SYSTEM menu and choose "About Ubuntu" expecting a splasch screen w/ a version no. and a dapper, hoary or whatever listed. NO. instead I get a page of bullet points about the OS. 

I tried a "ver" command on the terminal, but it's not recognized.

HOW DO I FIND MY VERSION?

oh yeah, I can't upgrade to the new version b/c the upgrade fails everytime---after i watch it d/l all kinds of files and do a bunch of stuff, then phhhhlllffft!

i did do a search on that a while ago and became even more confused.

Can you tell I'm frustrated?

---

### Post by simonn on 2006-08-31
> I'm usually pretty computer savvy.

Translation:

"I believe myself to be a windows 'Power User'"

Which, as you have discovered, does not mean that much in the linux world. 

> Can you tell I'm frustrated?

Yes, but do you think that will make people give up their own time to help you? See the link about asking smart questions in my sig.

I can only really guess at what you would like me to help you with, but try:

> 
$ sudo apt-get install gimp-help-en


---

### Post by etomic13 on 2006-08-31
You have the most recent version dapper is dapper drake which is the latest Ubuntu copy. For help wit gimp you must download it from synaptic. System-administrator-synaptic package manager. Then goto search tab and click search at the top and type in gimp and download the gimp files. (click check box then select apply)

---

### Post by fritz_monroe on 2006-08-31
To find the version of Ubuntu, do this.

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

```


Stick with it and do a little homework on your questions.  Like on most Linux forums, the folks here expect that the person asking the questions has done some homework first.

---

### Post by Lighthouse on 2006-08-31
the first two comments weren't much help, but I ran the cmd you suggested and something happened. however, at the end of that somehtign i got a bunch of lines that look like this:

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)


no idea what that means, but i'm guessing somehting couldn't be found.

so i open gimp and now when i click "help" i get nothing, nada, not even an error message. when i checked the file system i see that help files were indeed installed. I can now manually open the help's index page in firefox, but I'd really like to have the help open like it's supposed to.

___

Just a comment--how is one supposed to know that he can't use one of the two included GUI package installers to get the damn help files and he has to resort to an arcane terminal command instead?

---

### Post by Lighthouse on 2006-08-31
> **etomic13 said:**
> You have the most recent version dapper is dapper drake which is the latest Ubuntu copy. For help wit gimp you must download it from synaptic. System-administrator-synaptic package manager. Then goto search tab and click search at the top and type in gimp and download the gimp files. (click check box then select apply)

nope, i got breezy 5.1, thanks to the command provided by fritz

---

### Post by Lighthouse on 2006-08-31
> **fritz_monroe said:**
> To find the version of Ubuntu, do this.

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

```


Stick with it and do a little homework on your questions.  Like on most Linux forums, the folks here expect that the person asking the questions has done some homework first.

thanks for that. at least now i know i have breezy 5.10.
Really--should it be this hard? Why can't that stuff come up on "About Ubuntu"? every other app gives its version on the "About" page. try it and see what i mean. on the "about ubuntu" page I clicked the "Help" > "About" and got the version for YELP! and on the resulting page i saw version numbers for a bunch of ubu utilities and stuff. that's where my frustration was coming from.

I would like to get up to ubu 6, but like i said, whenever i try the upgrade option it fails. any suggestions on where to start to resolve taht one?

---

### Post by richbarna on 2006-08-31
> **Lighthouse said:**
> 
I would like to get up to ubu 6, but like i said, whenever i try the upgrade option it fails. any suggestions on where to start to resolve taht one?

Hi lighthouse,

Ok, you've got Breezy, but you want Dapper. The best way is to download it (the iso) and burn a fresh copy and install it instead of upgrading from Breezy (dist-upgrade).
[Here Is The Download and Burn Guide]("http://psychocats.net/ubuntu/iso.html")

I have done both, the new cd install is cleaner and less likely to cause problems. It is also a "live" cd which means you can even try it without installing by running it straight off the cd.

Her are some helpful links that will show you how to get started :-
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by blent07 on 2006-08-31
> **simonn said:**
> Yes, but do you think that will make people give up their own time to help you? See the link about asking smart questions in my sig.

After glancing at both links in your signature, I realize one stereotype that is true, whether or not it's already well-known: linux users are wordy. sometimes too wordy. a little verbose, a tab on the chatty side. 

A long webpage with a table of contents on how to ask a question? 
Awesome. You should be a lawyer :tongue: 

In that regard, I fit in rather well. ;)

---

### Post by click4851 on 2006-09-01
He posted in the correct forum, this is the "Absolute Beginner Talk" is it not. Certainly no one missed the Beginner Talk Rules sticky did they?

---

### Post by jISh on 2006-09-01
> **Lighthouse said:**
> 

Just a comment--how is one supposed to know that he can't use one of the two included GUI package installers to get the damn help files and he has to resort to an arcane terminal command instead?

I'm sorry I just have to say to that, terminal commands are what make Linux, not the X-server and GNOME desktop you see all the time. You will never have total control over your system until you see the power of the command line, and it is nothing "arcane". 

And you can install the help with Synaptic, if you had searched for "gimp" you would have found the docs in the repos!

---

### Post by click4851 on 2006-09-01
all well and true, and if this wasn't the " Absoulte Beginner Talk " forum, I would agree.

---

### Post by simonn on 2006-09-01
> **blent07 said:**
> 
A long webpage with a table of contents on how to ask a question? 
Awesome. 

You jest. Oh, the irony.

> You should be a lawyer :tongue:

Quite the opposite. 

Geeky types are wordy only when necessary. 

Lawyers are wordy so they can claim a different meaning later, if necessary.

---

### Post by mcduck on 2006-09-01
> **Lighthouse said:**
> 
Really--should it be this hard? Why can't that stuff come up on "About Ubuntu"? every other app gives its version on the "About" page. try it and see what i mean. on the "about ubuntu" page I clicked the "Help" > "About" and got the version for YELP! and on the resulting page i saw version numbers for a bunch of ubu utilities and stuff. that's where my frustration was coming from.
I just opened System/About Ubuntu and on the very first page it says 'Thank you for your interest in Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006.' ;)

And if you go to help menu in Yelp, you of course should get Yelp's help. Just like if you go to help menu in firefox you'll get firefox's help :)

---

### Post by hashimoto on 2006-09-01
> **mcduck said:**
> I just opened System/About Ubuntu and on the very first page it says 'Thank you for your interest in Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006.' ;)

But does/did Breezy have this in the Help? Seems like it doesn't and I can't blame a beginner for complaining...

---

### Post by blent07 on 2006-09-04
> **simonn said:**
> 

Quite the opposite. 

Geeky types are wordy only when necessary. 

Lawyers are wordy so they can claim a different meaning later, if necessary.

True, a much more realistic way of looking at it.

---

### Post by Lighthouse on 2006-09-04
> **hashimoto said:**
> But does/did Breezy have this in the Help? Seems like it doesn't and I can't blame a beginner for complaining...

I can attest that Breezy does NOT have this. at least the dev team learns fast.

---

### Post by bakert on 2006-09-04
So, did you get the gimp help installed?  What about the upgrade to Dapper?

---

### Post by Lighthouse on 2006-09-04
> **jISh said:**
> I'm sorry I just have to say to that, terminal commands are what make Linux, not the X-server and GNOME desktop you see all the time. You will never have total control over your system until you see the power of the command line, and it is nothing "arcane". 

And you can install the help with Synaptic, if you had searched for "gimp" you would have found the docs in the repos!

well i did use synaptic first. gimp showed up, but no help files. after installing the help via the cmd line i went back to synaptic and find a whole bunch of different gimp stuff and it shows my help files installed. weird.

about your first comment--i fully realize that the power of linux comes from the cmd line. i'm not afraid of the cmd line, but it's NOT easy to figure out what cmd to put on the line when things are unfamiliar. I DID do a search for the terms in the error msg i received but didn't get any satisfaction that way. THAT'S why i dropped into this beginner's forum.

i don't think the beginner's forum should be a place for snide remarks and an elitist attitude. Fritz answered one of my questions by just giving me the necessary cmd. no wasted bandwidth there.

i like linux. i use it nearly everyday. i do not use it exclusively. i like the idea that it is so powerful and i can do lots w/ it. SOmetimes, though, i just wanna get some damn work done--not fiddle around trying to reinvent the wheel.

---

### Post by Lighthouse on 2006-09-05
> **bakert said:**
> So, did you get the gimp help installed?  What about the upgrade to Dapper?

i did get the gimp help files installed. haven't had the free time to dapper up yet. i'm guessing it's going to require a fresh install from disk. <sigh> i had hoped to avoid that.

---

