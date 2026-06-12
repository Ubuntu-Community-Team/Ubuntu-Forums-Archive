---
title: "MS .net framework 2.0"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-28
I run Sony Vegas 7.0 (own all versions since 2.0) in XP Pro.  Would like to install this ap under Crossover.  During the install, I am prompted to download MS .net framework 2.0 and install it.  When I click the install  button, an error message pops up that state that "requirements not met" and crossover then prompts me to click ok to end the installation process.

I thought I might just search for this .framework think, download it separately and try to install it, but, when I get to the MS site, every possible option is presented except a download button.

Any suggestions on what I need to do to attempt to get this admittedly unsupported ap to install under Crossover?

Thanks.

Caruso

---

### Post by thegreenman on 2007-04-28
[http://www.microsoft.com/downloads/details.aspx?familyid=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=0856EACB-4362-4B0D-8EDD-AAB15C5E04F5&displaylang=en)

---

### Post by Najand on 2007-04-28
thegreenman:
Would you mind telling us the way to install that in linux... Obviousely he was not looking for a link.

---

### Post by carusoswi on 2007-04-28
So, trying to install the resultant download file for .net framework 2.0 results in another message asking for ms explorer 5.0.

More suggestions?

Caruso

---

### Post by wildkarde on 2007-04-28
perhaps a virtual machine?  that's my 2 cents. :/

---

### Post by rjfioravanti on 2007-04-28
mono is the way you run .NET applications on Linux

You can install mono from the repositories I believe, it is an open source implementation of the .NET framework

---

### Post by carusoswi on 2007-04-28
> **rjfioravanti said:**
> mono is the way you run .NET applications on Linux

You can install mono from the repositories I believe, it is an open source implementation of the .NET framework

Thanks for that tip.  I installed mono and retried the installation of my application.  The installation routine still called for the MS.  So far, I remain stumped.  

I can always boot into XP, but would love to get those few aps that I need to use working in Ubuntu.

Any additional comments or suggestions welcome.

Caruso

---

### Post by benton on 2007-04-28
I'd really love to see mono succeed on the Linux world. I am a C# / .NET programmer who would be really happy to see my programs run on Linux too. 

Unfortunately, the current mono version (1.2.xx) is way behind MS .NET Framework 2.0 in any way you would like to see it. Keep an eye on the mono roadmap though, perhaps a year from now the mono release will be 100% compatible with .NET 2.0. But then again, in a year from now, the current MS .NET framework is gonna be 3.5. :-(

Mono = very promising :-) but needs faster development. :-(

---

### Post by rjfioravanti on 2007-04-28
I think the mono in the repositories is quite behind. If you download the source version I think its 1.3 or .13 or something

Anyways I tried it in March and it worked really well with a .NET application I had developed

---

### Post by carusoswi on 2007-04-28
I went here to get it: [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

but didn't quite understand what to do once I got there.  Looked to me as though I should do what was described as a very simple install from code, but, didn't know how to get the given commands started in my terminal.

Thanks again for your advice to this point.

Additional help would also be appreciated.

Caruso

---

### Post by benton on 2007-04-29
> **rjfioravanti said:**
> I think the mono in the repositories is quite behind. If you download the source version I think its 1.3 or .13 or something

Anyways I tried it in March and it worked really well with a .NET application I had developed

Well actually I got their MOMA (mono migrating assistant) software to check some of my assemblies (built with MS.NET 2.0) for compatibility with the current mono version. 50% of the methods I use came up as mnono "todo". :(

---

