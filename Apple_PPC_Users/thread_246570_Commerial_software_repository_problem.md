---
title: "Commerial software repository problem?"
date: 2006-08-29
forum: Apple PPC Users
---

### Post by enderhegemon on 2006-08-29
Hi,

I installed the latest version of Ubuntu (6.06) and I have a problem with commercial software (ie installing Opera). "Add/Remove" software always specifies that "The 'dapper-commercial' software channel that includes 'Opera' is not enabled." Of course, I pressed enable. The canonical URI is listed in the repository section of Synatpic. Opera is not listed there, either. 

I also tried manually going through the process: inserting the proper text to the sources.list file, running sudo apt-get upate, sudo apt-get install opera. When I do that, I receive the following error message:

"Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate"

Any advice on how I should correct this problem?

---

### Post by Jagot on 2006-08-29
Could you post your sources.list here please?

---

### Post by linear on 2006-08-29
I could be way off, but browsing here: [http://archive.canonical.com/ubuntu/pool/main/o/opera/](http://archive.canonical.com/ubuntu/pool/main/o/opera/) suggests that there isn't a ppc package.

---

### Post by enderhegemon on 2006-08-29
> **Jagot said:**
> Could you post your sources.list here please?


deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Thanks.

---

### Post by enderhegemon on 2006-08-29
> **linear said:**
> I could be way off, but browsing here: [http://archive.canonical.com/ubuntu/pool/main/o/opera/](http://archive.canonical.com/ubuntu/pool/main/o/opera/) suggests that there isn't a ppc package.

That could be a problem.

---

### Post by Jagot on 2006-08-29
OK.  Your sources.list looks fine to me.  I think, as linear suggested, that the repository only delivers opera for i386 that is causing the issue.  You can download a .deb of Opera for PPC from opera.com.

---

### Post by enderhegemon on 2006-08-30
> **Jagot said:**
> OK.  Your sources.list looks fine to me.  I think, as linear suggested, that the repository only delivers opera for i386 that is causing the issue.  You can download a .deb of Opera for PPC from opera.com.

Yeah, it does make sense. Unfortunately, I did just try to install Opera by downloading the package and it won't load. It's not a big deal, but still would have been nice.

Thanks for your time and help.

---

### Post by casta_baga on 2006-12-02
> **enderhegemon said:**
> Yeah, it does make sense. Unfortunately, I did just try to install Opera by downloading the package and it won't load. It's not a big deal, but still would have been nice.

Thanks for your time and help.


I'm having the same problem.. it install but does not start

I'm actually getting an error during installation error: conflits with the installed package 'opera'

did u figure anything out?

i'm very disappointed with this ubuntu thing, unfortunately...
lots of work to get things running all the time, to install plug in on firefox is a pain, browsing and watching media on-line theres no way... i'm thinking about erasing this ubuntu from my powerbook and just stick with macX... unfortunately ... i'm kinda of interested in this ubuntu...

---

### Post by enderhegemon on 2006-12-03
Hi casta_baga,

Actually, Ubuntu worked quite well for me. I can't recall my exact solution for Opera, but it was something relatively simple. If you haven't done so already, write down the error message(s) and look for that phrase on Google (or the search engine of your choice). 

Media on the web was a problem. Plug ins refused to work, but I was able to watch most of the videos "offline." Since the Flash player isn't available for the PPC platform sites like YouTube are useless.

Overall, my experience with Ubuntu was positive. For many issues, there's an answer somewhere, which is great. Keep at it, if anything, your general knowledge of computers will increase.

Good luck.

---

