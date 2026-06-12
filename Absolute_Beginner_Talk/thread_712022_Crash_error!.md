---
title: "Crash error!"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2008-03-01
I've upgraded my ubuntu 7.10 to 8.04! The update-manager can't be upgraded en I get this error:
>  USER$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  update-manager
The following packages will be upgraded:
  update-manager
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/895kB of archives.
After this operation, 49.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 111818 files and directories currently installed.)
Preparing to replace update-manager 1:0.81 (using .../update-manager_1%3a0.87.10_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1685, in <module>
    main()
  File "/usr/bin/pycentral", line 1679, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1180, in run
    pkg.prepare(used_runtimes, old_used_runtimes, old_pkg)
  File "/usr/bin/pycentral", line 803, in prepare
    rt.remove_byte_code(removed_fs)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.87.10_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.87.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Could someone help me?

---

### Post by Cypher on 2008-03-01
I'm just curious as to why you attempted to upgrade from the stable 7.10 Gutsy to the unstable 8.04 Hardy? Upgrading to the latest unstable base is only recommended for people well versed with Linux as there are bound to be many issues that need to be addressed before the release.

Having said that, you might want to check out Launchpad to see if there are any issues with Hardy's update-manager to get your fix. Or revert back to the Gutsy until Hardy is officially released..

---

### Post by linux-beginner on 2008-03-01
I've just looked at  Launchpad! But there are any errors such this error!

---

### Post by buckykat on 2008-03-01
i had the same error you do, but i found a fix (perhaps not the best one, but eh). i logged out, switched the session to kde(i have both gnome and kde variants installed, i find it comes in useful sometimes), and fired up the kde update utility. it not only got update-manager fixed, but finished the rest of the update. hope this helps.

---

### Post by candyban on 2008-03-10
You can use the following command from the command line:

# dpkg --ignore-depends=update-notifier --remove update-manager && apt-get install update-manager

When the previous command complains about other dependencies, you should check the output and add multiple ignore-depends statements:

e.g. Mythbuntu:

"# dpkg --remove update-manager" will give an output like this:

dpkg: dependency problems prevent removal of update-manager:
 **mythbuntu-desktop depends on update-manager**.
 [COLOR="RoyalBlue"]update-notifier depends on update-manager[/COLOR]; however:
  Package update-manager is to be removed.
dpkg: error processing update-manager (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 update-manager

The resulting command would then become:
# dpkg --ignore-depends=[COLOR="RoyalBlue"]update-notifier[/COLOR] --ignore-depends=**mythbuntu-desktop** --remove update-manager && apt-get install update-manager

Hope this helps.

---

