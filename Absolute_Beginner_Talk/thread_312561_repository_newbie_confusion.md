---
title: "repository newbie confusion"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2006-12-04
Hi all!

I'm a little confused about the whole repository thing; I've had my Ubuntu installation running for a few days now and would like to add some extra programs.

I've read a number of places describing the differences between main, restricted, universe and multiverse and how to add repositories, however I'm a little confused as to exactly what my system is set up to use, and what I want.

If I go to system/administration/software preferences then I have the following list of repositories (on the installation media tab):

    CD disk with Ubuntu 6.06 LTS (Binary)
        officially supported
        restricted copyright
    CD disk with Ubuntu 6.06 LTS (Binary)    <not a typo, there are two copies of this one that appear identical>
        officially supported
        restricted copyright
    Ubuntu 6.06 LTS (Source)
        officially supported
        restricted copyright
    Ubuntu 6.06 LTS Updates (Binary)
        officially supported
        restricted copyright
    Ubuntu 6.06 LTS Updates (Source)
        officially supported
        restricted copyright
    Ubuntu 6.06 LTS (Binary)
        community maintained (universe)
        officially supported
        restricted copyright
    Ubuntu 6.06 LTS (Source)
        officially supported
        restricted copyright
        community maintained (universe)

along with a couple named 'backports' and 4 with 'security', with various combinations of officially supported, restricted and universe.

Do I need all these to be there?  If I'm not interested in compiling programs at this stage can I/should I remove the ones that say 'source' after them? and what is the difference between all the different entries?

If there is a post/article somewhere that explains this in detail already then feel free to point me at it - I just haven't found one that seemed to fit my situation and that I understood ;)

---

### Post by bruenig on 2006-12-04
It doesn't hurt to have all of them. It allows you to access any package you need. As far as the source repositories, it doesn't really matter if those are enabled or not. The only time those come into play is if you do sudo apt-get source package. If you don't want the source, sudo apt-get install will do fine. Or if you use synaptic, it will just install the binaries. So you can remove that or the leave them, doesn't really matter.

---

### Post by CatKiller on 2006-12-05
[This page]("https://help.ubuntu.com/community/Repositories") explains in general terms what an online repository is. [This one]("http://monkeyblog.org/ubuntu/installing/") gives you some practical information on what you can do with them.

The classes of repository (main, restricted, universe and multivers) describe the class of software that is contained therein - how free it is and whether Canonical support it. The categories (Updates, Security, Backports and so on) define the function of the repository. So Backports is for packages that are updated for newer versions of Ubuntu, and then ported to older versions, the Security Updates repository is for Security Updates and so on. It is also possible to add other repositories to your list (sources.list) should you wish.

I hope this helps make it a bit clearer, and welcome to the community.

---

### Post by Big_Croc7 on 2006-12-05
Brilliant, yes that makes things clearer :-)

Thankyou both :)

---

