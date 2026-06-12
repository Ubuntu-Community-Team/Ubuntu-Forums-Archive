---
title: "as Default installed list"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-04-12
Hi All,

I have noticed that, Perl, LibXML parser are all installed as default with my Ubuntu Linux version.

May I know what is the reason for installing such programmes and parsers as default with Linux OS?

Also, is it possible for me to get the list of programmes, parsers and Applications which are all installed as default with OS installation?

Thanks in Advance,
Srikrishnan

---

### Post by smartboyathome on 2008-04-12
I think it is installed by default because a program needs it. If it didn't, then it most likely wouldn't be installed by default.

---

### Post by srikrishnan on 2008-04-12
hi,

Is it possible for me to get the list of softwares (Programmes, Parsers, and Applications) installed as Default with my OS? as well as which are all needs for what purpose?

Regards,
Srikrishnan

---

### Post by Sukarn on 2008-04-12
I think perl, python and such interpreters are installed by default because a lot of applications need them.

About the list of software packages installed by default in Ubuntu - I don't think its ever come up before. At least I've never bothered looking for it.

---

### Post by shivam.seth on 2008-04-12
All these packages are required for some applications to work. They are called dependencies...i.e. without these packages, you cannot install some other packages. Many applications are developed in perl and that is the reason you find it installed by default despite the fact that you don't need it.

For viewing a list of all the packages installed in your system, you can open the Synaptic Manager and just select 'Packages installed'...this will show you all the packages installed and if you click on a package, it will show you its description and need!

Hope this answers your query!

---

### Post by conscious on 2008-04-12
To see the list of all installed packages: ```
dpkg -l
```

---

### Post by srikrishnan on 2008-04-12
Hi,

Package manager GUI as well as command line syntax "dpkg -l" are displaying all the packages, modules which required for OS, But i need to know only the standalone softwares like Perl, LibXML parser, etc.

Regards,
Srikrishnan

---

### Post by hyper_ch on 2008-04-12
you mean what the dependencies are for perl?

---

### Post by Sukarn on 2008-04-13
No, we mean that other softwares depend on perl.

Also, there are some packages that perl itself depends on. Too see what a particular package depends on, open "synaptic", and right click on a package name, click on "properties", and go to the tab named "Dependencies".

To view which packages depends on the package you have selected, click on the drop down box that says "Dependencies" and select "Dependent packages"

---

