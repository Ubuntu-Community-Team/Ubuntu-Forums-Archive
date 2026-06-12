---
title: "Help - installing R in ubuntu 6.06 dapper"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by olechnwin on 2007-10-02
I need help installing r statistical software
I was able to add "deb [http://CRAN.R-project.org/bin/linux/ubuntu](http://CRAN.R-project.org/bin/linux/ubuntu) dapper/" to /etc/apt/sources.list
then run sudo apt-get update but I got the following error:
W: GPG error: [http://CRAN.R-project.org](http://CRAN.R-project.org) dapper/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821
W: You may want to run apt-get update to correct these problems

I tried to add different sites to sources.list such as "deb [http://cran.stat.ucla.edu/bin/linux/ubuntu](http://cran.stat.ucla.edu/bin/linux/ubuntu) dapper/" and "deb [http://cran.cnr.berkeley.edu/bin/linux/ubuntu](http://cran.cnr.berkeley.edu/bin/linux/ubuntu) dapper/" but got the same error. 

Can you tell me how to fix this problem. R software website is [http://www.r-project.org/]("http://www.r-project.org/") 

Thank you in advance for your help

---

### Post by mali2297 on 2007-10-02
R is available in the universe repository, just install the package **r-base** through Synaptic or by
```

sudo apt-get install r-base

``` 

You don't need to add "deb http://CRAN.R-project.org/bin/linux/ubuntu dapper/" in your sources.list unless you want the very latest version of R. In that case, I think you also need to run
```

gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg -a --export E2A11821 | sudo apt-key add -
sudo apt-get update

```  
in the terminal. (Instructions from [here]("http://cran.r-project.org/bin/linux/ubuntu/").)

---

### Post by olechnwin on 2007-10-03
**mali2297**, thank you so much for your help. I tried to do what you suggested but I am still stuck. 
I tried gpg --keyserver subkeys.pgp.net --recv-key E2A11821 and it's complaining about keyserver error (I guess just like what was mentioned on their website, it was blocked by firewall). So, I tried the next thing to get the key from [http://keyserver.noreply.org/](http://keyserver.noreply.org/) then run sudo apt-key add key.txt but I got another error: gpg: no valid OpenPGP data found.

So, I gave up that route then tried to install using sudo apt-get install r-base (being a newbie in this I didn't know this command before) but I got yet another error:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  r-base: Depends: r-base-core (>= 2.5.1-2dapper0) but it is not going to be installed
          Depends: r-recommended (= 2.5.1-2dapper0) but it is not going to be installed
E: Broken packages

I played around with synaptic,since you mentioned that was another way I can get R installed, but I got similar error message as above. Please help...:confused:

Thanks

---

### Post by mali2297 on 2007-10-03
First of all, remove the line you added in sources.list. Then try to run the following in the terminal:
```

sudo apt-get update
sudo apt-get install -f r-recommended

```

---

### Post by olechnwin on 2007-10-04
> **mali2297 said:**
> First of all, remove the line you added in sources.list. Then try to run the following in the terminal:
```

sudo apt-get update
sudo apt-get install -f r-recommended

```

I tried to do the above and got another error about the package cannot be found.

Here is the output:

ny@lb-off-lx:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
ny@lb-off-lx:~$ sudo apt-get install -f r-recommended
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package r-recommended

---

### Post by mali2297 on 2007-10-04
Have you enabled the universe repository? 

In Synaptic, you can do that through the menu Settings > Repositories (or something like that). See here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then search for r-base and r-recommended, they should both be there.

---

### Post by olechnwin on 2007-10-05
**mali2297** :KS, Thank you so much for all your help. I can finally install R. Also, thank you for pointing out all those websites. I thought in order to install R you need to follow the direction from their website without knowing anything about synaptic and repositories thing. That's what messed me up. For now I am content with the R from the repositories. Next time I'll probably know where to look for instructions. Thanks for helping a newbie:smile:

---

