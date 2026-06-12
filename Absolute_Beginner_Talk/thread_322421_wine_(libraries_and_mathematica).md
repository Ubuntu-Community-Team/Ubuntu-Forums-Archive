---
title: "wine (libraries and mathematica)"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Ruth Lazkoz on 2006-12-20
Hi,

Installed wine and I can see my window partition OK.

Now, from the directory where mathematica is installed I type for instance 

wine MathKernel.exe and I get what I shown here


ruth@ruth-desktop:/windows/WolframResearch/Mathematica/5.2$ wine MathKernel.exe
err:module:import_dll Library ML32I2.dll (which is needed by L"Z:\\windows\\WolframResearch\\Mathematica\\5.2\\MathKernel.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\windows\\WolframResearch\\Mathematica\\5.2\\MathKernel.exe" failed, status c0000135

I tried to copy the ML32I2.dll library in /usr/lib (with the correct capitalization) and got no success.

Any hint?

Thanks,

Ruth

---

### Post by dienush on 2006-12-20
The linux version of mathematica is included on the mathematica cd and works just fine as long as num-lock is off.  

If you still want Mathematica to work under wine, it might fix your problem if you have your C drive mappings correctly configured.  Something like:

winecfg
select 'MathKernel.exe'
select 'drives tab'
make sure letter C: points to the mount point of your windows partition/drive

I ran into trouble with wine when doing this since my mathID under wine was different than my mathID under XP, and hence mathematica wouldn't verify my license.  If you want to switch to using mathematica under linux, I heartily recommend installing the linux version and looking at this for transferring your license: 

[http://www.wolfram.com/services/customerservice/systemtransferus.html](http://www.wolfram.com/services/customerservice/systemtransferus.html)

It's pain to fax that form, but it's worth it for such an amazing piece of software!  Hope this helps!

Dave

---

### Post by Ruth Lazkoz on 2006-12-21
> **dienush said:**
> The linux version of mathematica is included on the mathematica cd and works just fine as long as num-lock is off.  

If you still want Mathematica to work under wine, it might fix your problem if you have your C drive mappings correctly configured.  Something like:

winecfg
select 'MathKernel.exe'
select 'drives tab'
make sure letter C: points to the mount point of your windows partition/drive

I ran into trouble with wine when doing this since my mathID under wine was different than my mathID under XP, and hence mathematica wouldn't verify my license.  If you want to switch to using mathematica under linux, I heartily recommend installing the linux version and looking at this for transferring your license: 

[http://www.wolfram.com/services/customerservice/systemtransferus.html](http://www.wolfram.com/services/customerservice/systemtransferus.html)

It's pain to fax that form, but it's worth it for such an amazing piece of software!  Hope this helps!

Dave

Hi,

I would actually prefer to use the linux version, which I installed succesfully and is running. The problem to me at least is that the fonts in the menu look horrible. I am pretty new to linux but I think it should be possible to change an .Xsomething file to make this fonts look good, 

So, if you have it running you could perhaps give me a hint to do this modification, that is, which is the file I have to modify and what modification is required (assuming it is possible).

Thanks,

Ruth

---

