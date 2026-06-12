---
title: "Software doesn't run in Edgy"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by useResa on 2006-12-17
I have posted a [thread]("http://www.ubuntuforums.org/showthread.php?t=319931") in General Help regarding (third party) software no longer working in neither Edgy nor Feisty, while it was working with no problems in Dapper.
Due to the little response I got I guess that the question was maybe not asked in the right section. Therefor let me first ask a general question:

[COLOR=Navy][I]What is the  best section to post a thread when software is no longer working in Edgy and/or Feisty?
[/I][/COLOR]

---

### Post by lamego on 2006-12-17
Just to clear things up, Ubuntu X being based on Debian Y doesn't mean all applications will run fine on both, it all depends if they need a specific library or kernel version which may be different between Debian and Ubuntu...
>     * Can anyone help me solve this issue? I would like to remain using Ubuntu, but if the main software for doing my job doesn't work in Ubuntu I have a serious problem.
    * What sort of information can and/or should I provide in order to help you indicate the cause?
Running the software from the terminal and posting the error messages is always a good place to start...

---

### Post by useResa on 2006-12-17
> **lamego said:**
> Just to clear things up, Ubuntu X being based on Debian Y doesn't mean all applications will run fine on both, it all depends if they need a specific library or kernel version which may be different between Debian and Ubuntu...
I am aware of the fact that this is the case.
My main issue as such is the fact that it used to work fine in Dabber and stopped working as of Edgy.

> **lamego said:**
>  Running the software from the terminal and posting the error messages is always a good place to start...
If I start the software from the terminal, the same error text as reflected in the software's log file is printed.
> Stack overflow detected In Task ( EVENTTSK ]
Fault and traceback information not available
Task Traceback

FATAL ERROR: WRCODE=80000803, MODULE='vtinit': Cannot Create event task

Traceback

No Traceback Available

Stack overflow detected In Task ( sasxkern ]
Fault and traceback information not available
Task Traceback

Stack overflow detected In Task ( EVENTTSK ]
Fault and traceback information not available

Is there any other way to get more debugging information?

---

### Post by x64Jimbo on 2006-12-17
Well, many programs have debugging options. I highly suggest putting in a support request with the software developer or reading the documentation for it, and seeing if you can find a debugging option.

---

### Post by useResa on 2006-12-17
> **x64Jimbo said:**
> Well, many programs have debugging options. I highly suggest putting in a support request with the software developer
With "software developer" you mean someone at SAS Institute or do you mean an Ubuntu software developer?

> **x64Jimbo said:**
>  or reading the documentation for it, and seeing if you can find a debugging option.
We have gone over all possible options and ran out of options, hence these posts in the UF.

---

### Post by x64Jimbo on 2006-12-17
SAS Institute, since it's a third party program not installed in Ubuntu by default or in the repos.

---

### Post by useResa on 2006-12-17
> **x64Jimbo said:**
> SAS Institute, since it's a third party program not installed in Ubuntu by default or in the repos.
Clear. Thank you, I'll try that route.

[COLOR=Navy]**BTW:** Should anyone have any other suggestions, please feel free to post your suggestion![/COLOR]  ;)

---

### Post by x64Jimbo on 2006-12-17
Of course! No one should hesitate to give an answer if they have one. However, can you give the name of the software and the version so that others may be able to help you?

---

### Post by useResa on 2006-12-18
> **x64Jimbo said:**
> However, can you give the name of the software and the version so that others may be able to help you?

The software is [SAS Software](http://www.sas.com).
The version I am running is Release 8.2 (TS2M0).

---

