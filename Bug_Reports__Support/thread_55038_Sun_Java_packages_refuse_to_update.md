---
title: "Sun Java packages refuse to update"
date: 2005-08-07
forum: Bug Reports / Support
---

### Post by sebb on 2005-08-07
When installing sun-j2re1.5 and sun-j2sdk1.5 (1.5.0+update04) I get the following error messages:

```
Setting up sun-j2re1.5 (1.5.0+update04) ...
mv: cannot stat `firefox-javaplugin.so': No such file or directory
update-alternatives: unable to rename firefox-javaplugin.so to /usr/lib/mozilla-firefox/plugins/libjavaplugin.so: Invalid cross-device link
dpkg: error processing sun-j2re1.5 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up sun-j2sdk1.5 (1.5.0+update04) ...
mv: cannot stat `firefox-javaplugin.so': No such file or directory
update-alternatives: unable to rename firefox-javaplugin.so to /usr/lib/mozilla-firefox/plugins/libjavaplugin.so: Invalid cross-device link
dpkg: error processing sun-j2sdk1.5 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-j2re1.5
 sun-j2sdk1.5

```

I know I did some manual fiddling with Firefox and Java to make Firefox load the Java plugin, but I cannot quite recall what I may have done to break update-alternatives. How can I get rid of that annoying message (that does not keep Firefox from loading the java plugin for whatever reason)

Thanks in advance

---

