---
title: "Compile a newer version of synergy for PPC"
date: 2011-05-23
forum: Apple Hardware Users
---

### Post by clarissa.w on 2011-05-23
Hi there

I would like to know how or given directions how to compile a newer version of synergy for PPC. Or it would be nice if someone could compile it though I want to learn how to do these things.

Synergy is available for download from: [http://synergy-foss.org/download/](http://synergy-foss.org/download/)


Thanks

---

### Post by pauljwells on 2011-05-23
Isn't there already a version in the repositories? Natty PPC has v1.3.6 for example. Trying to install a much newer version could damage your system so be very careful. It looks like everything gets installed into /usr/local/bin and if you've not done anything like this before then that directory is probably empty. Check it first then you can see what new stuff gets installed so you know what to delete if it all goes pear-shaped.

If you want to have a go at compiling, the best way is first to try and compile the same version as your version of Ubuntu already has. This will ensure you have a sane build system and all the dependencies needed (mostly...) This way also creates debs so you can install and uninstall easily.

[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/")

Once you've done that you can download the source from the site to which you linked. It looks quite straightforward: unpack the source to a directory, cd into it and run the command

```
./lm.sh build
```

If there are any new dependencies that weren't needed by the packaged version then these will show up in the output (package foo not found) XTest might be such a package. You'll need to install the -dev versions which you can do easily in synaptic.

It's not completely clear how you actually install it once it's compiled :-S but I would try

```
sudo make install
```

as the build process looks like it uses the 'make' command internally. Building from source like this won't produce the nice tidy deb files unfortunately.

I have a PPC G5 system at home but I'm away for a few weeks otherwise I would have had a go for you.

Good luck, post back with questions and reports.

---

### Post by clarissa.w on 2011-05-23
When I last looked a week ago, it was an older version - 1.3.1. I am using Ubuntu 10.04 LTS

Thanks for replying

I will try what you suggested.

---

