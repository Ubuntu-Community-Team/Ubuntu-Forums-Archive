---
title: "Synaptic installs firefox plugins into wrong directory"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by angelboy on 2006-09-07
I have this problem: everytime I install a plugin for mozilla firefox (with apt-get or synaptic), plugins goes to wrong directory (usr/lib/mozilla/plugins). Right directory should be /opt/firefox/plugins where I installed (and updated) the firefox from mozilla website.

How ever, I have copied the plugin files from /usr/lib/mozilla/plugins to the /opt/firefox/plugins and then the plugins have usually worked. But not java-plugin. I've copied the libjavaplugins.so to correct directory with no luck. I have tried symbolic links etc. guides that I've found from net. No luck either.

So the problem is, how can I change the "default" firefox path to /opt/firefox and how can make the java plugin working?

---

### Post by monktbd on 2006-09-07
if you install firefox from synaptic then the plugins will go into the right directory.

the *.deb packages in the ubuntu repos are tailored for each other and cannot take care of where the binary of the mozilla website installs itself.

---

### Post by angelboy on 2006-09-07
I installed firefox from mozilla website 'cause some people said that it is faster that ubuntu firefox... I don't know if it is.

So anyway, I think that I have both foxes on my ubuntu now, 'cause I didn't uninstall anything. How can I remove firefox which i downloaded from mozilla.com? Just delete /opt/firefox folder? And does the firefox then work if i reinstall it from the synaptic? Is there 1.5.0.6 version available in synaptic?

Just wondering, is there a manual way to install plugins to correct directory from terminal?

---

### Post by monktbd on 2006-09-07
i am not sure whether deleting the firefox folder would get rid of everything that firefox installed. also i dont knwo whether there is an uninstall script with the binary installer from the website.

about the plugins:
i never had a problem with java working with the symbolic link. right now it is also a symbolic link to
> lrwxrwxrwx 1 root root     39 2006-07-15 23:28 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so

keep in mind that in your home folder there is also a .mozilla folder. maybe you have some plugins there as well? i am quite sure those settings override the general settings in either /opt or /usr.

the current version on my system is:
> Mozilla Firefox 1.5.0.5, Copyright (c) 1998 - 2006 mozilla.org

i myself dont see the necessity to upgrade to a newer version.
the benefits of having a *.deb that does security updates more or less automatically via apt-get/synaptic outweighs any small improvements a newer version might have.

---

### Post by angelboy on 2006-09-07
I got the javaplugin working now by making that symbolic link which you had. Thanks a lot =)

---

