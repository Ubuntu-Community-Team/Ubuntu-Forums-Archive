---
title: "What does sudo dpkg -i  Do?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-19
Im having trouble installing applications. iv read around, and iv noticed when people are trying to install .deb files, this is what is recommended.

im just wondering, what does this sudo dpkg -i actually mean and what does it do?

I just treid doing this, but the terminal said 

```

dpkg: dependency problems prevent configuration of <app name>
<app name> depends on libstdc however
package listdc++5 is not installed


```

Im guessing this means i need to install this "listdc" thing? and how would i do that? 

Thanks :)

---

### Post by n0dl on 2006-10-19
sudo dpkg -i installs a .deb package that you have fetch from somewhere on the internet. basically that error message is saying that it does not have the dependencies that it is looking for. This is caused by either the developer not giving the package dependency resolve or it is not installing the dependency due to stability issues. Try sudo build-dep pkg then try sudo dpkg -i pkg.

---

### Post by Tobywuk on 2006-10-19
Does that mean that i cant do anything but just try and get another version of the .deb package?

thanks :)

---

### Post by ATAQ on 2006-10-19
NO, it means that you need the listdc++5 as a dependancy in order for the application to work. you can apt-get it

---

### Post by Tobywuk on 2006-10-19
just did apt-get for that and i got

```

the following packages have unmet dependencies:
libstdc++5: depends gcc-3.3-base but it is not going to be installed
E: unmet dependencied. try 'apt-get -f install'

```

i tried the -f bit but it dident work

What does this mean? how do i get round this?

---

### Post by DarkN00b on 2006-10-19
Whenever I install a .deb, I just doubleclick it and let the gdebi package manager handle the dependencies.

---

