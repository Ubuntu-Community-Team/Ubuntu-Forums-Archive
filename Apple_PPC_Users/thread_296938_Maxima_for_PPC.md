---
title: "Maxima for PPC"
date: 2006-11-10
forum: Apple PPC Users
---

### Post by engla on 2006-11-10
The Problem: Maxima doesn't run at all on the powerpc architecture.

I came here because I'm very disappointed with the Ubuntu release managers and universe managers; this is not a simple slip-up, but the bug has been known since march-april, and in neither dapper or edgy is the maxima version from the repositories working. Nothing has been done to ship a working version (like the, for me, acceptable solution of shipping an old but working version).

The bottom line: You have to grab maxima, maxima-share and maxima-doc from breezy or hoary or some debian source. No fun, and it breaks the other repo tools that depend on maxima.

What I want to do is foremost bring attention to this issue; I want it to be solved in any way, I just want the repository version to work, whatever the version. I don't understand the neglect at all, it's been two major releases (edgy and dapper LTS!).

Secondly, I also want your offers on this, on where to go for the best alternative maxima package (I would love wxmaxima support too), and perhaps someone of you can help with the actual blocker bug itself, or perhaps you can help bringing maxima 5.10 into ubuntu (I suspect from debian the bug is fixed here).

The bug link: [https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169](https://launchpad.net/distros/ubuntu/+source/maxima/+bug/37169)

thanks.

---

### Post by kellogs on 2006-11-14
Hi, I compiled maxima 5.10.0, wxmaxima (last version) and GCL clisp on powerpc. 

There is a problem with dapper repositories, I dont know the state of things in edgy. I had to compile GCL(last version) manually and even apply a debian patch(diff2.7.22) that miraclously worked well. 

If you try to aptget clisp on dapper (dont know in edgy) it is completely broken, there is no CMUCL in repos on ppc, and SBCL does compile but had problems! :eek: !!

So the panorama in ppc was not pretty good to make work maxima if you are an scientist or mathematician or programmer, you are pretty stuck, because its the only "good" symbolic algebra program in linux.

If you look at the end of the launchpad thread you posted above you will see that maxima at the moment works in ppc only with GCL, and the GCL in dapper is being fixed (still) and there is quite a mess with gcl in ppc in dapper that everybody is complaining about :eek: .

My advice is, download GCL from debian unstable and apply last patch, and then download maxima and wxmaxima last versions from official sites and compile normally, problem fixed. at launchpad people is still complaining and raving about why this haven't been fixed!:eek: :o :eek: 

If you still have problems I can upload the debs to rapid share or something like that(I dont have proper webspace lol), only tell me.

cheers.

---

### Post by engla on 2006-11-15
Thanks for your answer -- I'll see if I can try compiling all that again. Last time I ran into some compilation error and gave up; lisp is not my thing so I dropped that. 

It would be great if you could send the debs, but I don't know how that will work with my edgy.

---

### Post by kellogs on 2006-11-15
I know, Lisp compiling sucks in the lisp way, but Gcl can be compiled via configure, make, make install. only you have to --enable-ansi thing in configure(if I remember well). 

if you have problems I've got GCL with ansi enabled, and Clisp 2.40 compiled too. 

I dont know if it will be any dependency problem to you, but probably not nothing you can't get from synaptic.

If you need it send me a p.m. and I will send you the debs, no prob. 

pd: Im the autor of the last ppc solutions on the launchpad thread, I was 3 months or more waiting for a maxima fix in dapper that never came, so I had to compile all clisps and all maxima's that were available in dapper and then compiling with source updated version with a bit more luck.

sorry about my english, im spanish.

---

