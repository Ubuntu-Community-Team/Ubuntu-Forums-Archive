---
title: "somehow can't install program in terminal"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by secret_force on 2006-08-05
I'm trying to install dvdauthor on my kubuntu 6.06 machine. I'm doing this in the terminal as there is no repository. I've installed many programs already in the terminal, so I know about ./configure --> make --> make install. This time, however i get a message that i never got before, due to this message the program doesn't install. This is what the terminal writes, after I type "make"

[I]Making all in doc
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/doc' wordt binnengegaan
make[1]: Er is niets te doen voor 'all'.
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/doc' wordt verlaten
Making all in src
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/src' wordt binnengegaan
make  all-am
make[2]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/src' wordt binnengegaan
make[2]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/src' wordt verlaten
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/src' wordt verlaten
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11' wordt binnengegaan
make[1]: Er is niets te doen voor 'all-am'.
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11' wordt verlaten
ernst@ernst-desktop:~/Desktop/dvdauthor-0.6.11$ make install
Making install in doc
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/doc' wordt binnengegaan
make[2]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/doc' wordt binnengegaan
make[2]: Er is niets te doen voor 'install-exec-am'.
test -z "/usr/local/share/dvdauthor" || mkdir -p -- . "/usr/local/share/dvdauthor"
mkdir: kan map `/usr/local/share/dvdauthor' niet aanmaken: Toegang geweigerd
make[2]: *** [install-dist_pkgdataDATA] error 1
make[2]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/doc' wordt verlaten
make[1]: *** [install-am] error 2
make[1]: Map '/home/ernst/Desktop/dvdauthor-0.6.11/doc' wordt verlaten
make: *** [install-recursive] error 1
ernst@ernst-desktop:~/Desktop/dvdauthor-0.6.11$    [/I]    

Does anyone know what's wrong??

---

