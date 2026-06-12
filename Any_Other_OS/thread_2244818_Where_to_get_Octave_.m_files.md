---
title: "Where to get Octave .m files ?"
date: 2014-09-18
forum: Any Other OS
---

### Post by Kieroneil on 2014-09-18
My version of Octave didn't come with any function files.  I'm trying to use the roots() function and will probably need many others.  Where can I download these files so I can use the functions in them?

Thanks.

---

### Post by Kieroneil on 2014-09-18
My version of Octave didn't come with any function files.  I'm trying to use the roots() function and will probably need many others.  Where can I download these files so I can use the functions in them?

Thanks.

---

### Post by oldfred on 2014-09-18
Looks like Forum hiccuped, or you posted twice. Merged double entry.

---

### Post by steeldriver on 2014-09-19
Hello and welcome to the forums

What version of octave and where did you get it? What version of Ubuntu?

It should be part of the octaveN.m-common package e.g. on 12.04

```

octave:1> help roots
`roots' is a function from the file /usr/share/octave/3.2.4/m/polynomial/roots.m

$ dpkg -S /usr/share/octave/3.2.4/m/polynomial/roots.m 
octave3.2-common: /usr/share/octave/3.2.4/m/polynomial/roots.m

```

---

### Post by Kieroneil on 2014-09-19
I'm almost embarrassed to say that the version is 3.2.4 and I got it as part of some Linear Algebra class I had taken in the past.  I'm also running it on Windows.

Would you suggest that I install the latest version?

---

### Post by steeldriver on 2014-09-19
Moved to **Other operating systems and projects** since it does not appear to be about Ubuntu

I can confirm that the roots function is available in the standalone port for Windows v. 3.6.2 - that's the only Windows version I have access to at the moment

[URL="http://sourceforge.net/projects/octave/files/Octave%20Windows%20binaries/"]http://sourceforge.net/projects/octave/files/Octave%20Windows%20binaries/
[/URL]
 If you are using octave via cygwin the answer may be different

---

### Post by Kieroneil on 2014-09-19
I have downloaded the latest Windows build, checked to see that the Polynomials file is in the path, and checked to see that the polynomials file actually exists in that location.  I'm now beginning to think that I'm calling it wrong.  

This is what I am doing:
m = ([3,4; 5,2])
roots(m)

The error I get is: Invalid call to roots.  Correct usage is:

-- Function File:  roots (V)

---

### Post by steeldriver on 2014-09-19
AFAIK 'roots' only works on a vector (i.e. a single polynomial at a time) - you will get the same error in matlab I think

```

octave-3.6.2.exe:10> m = [3,4;5,2]
m =

   3   4
   5   2

octave-3.6.2.exe:11> roots(m)
error: Invalid call to roots.  Correct usage is:

 -- Function File:  roots (V)


Additional help for built-in functions and operators is
available in the on-line version of the manual.  Use the command
`doc <topic>' to search the manual index.

Help and information about Octave is also available on the WWW
at http://www.octave.org and via the help@octave.org
mailing list.
octave-3.6.2.exe:11>

```

but
```

octave-3.6.2.exe:11> roots([3,4])
ans = -1.3333
octave-3.6.2.exe:12> roots([5,2])
ans = -0.40000
octave-3.6.2.exe:13>

```

---

### Post by Kieroneil on 2014-09-19
I appreciate the quick responses.  I am taking a course on Electric Circuits on EdX and one of the quiz questions is this:
[COLOR=#3C3C3C][FONT=Open Sans]The characteristic roots of the matrix [/FONT][/COLOR][COLOR=#888888][FONT=Open Sans][/FONT][/COLOR][COLOR=#3C3C3C][FONT=Open Sans][FONT=MathJax_Size3]([/FONT][FONT=MathJax_Main]3[/FONT][FONT=MathJax_Main]5[/FONT][FONT=MathJax_Main]4[/FONT][FONT=MathJax_Main]2[/FONT][FONT=MathJax_Size3])[/FONT][/FONT][/COLOR][COLOR=#3C3C3C][FONT=Open Sans] are 7 and ______ respectively.
I thought that the roots function would answer this.  Does anyone happen to know what function in Octave or Matlab I should use?[/FONT][/COLOR]

---

### Post by Kieroneil on 2014-09-19
FYI...The matrix in my previous post didn't print correctly but it is [3,5;4,2]

---

### Post by steeldriver on 2014-09-19
The 'roots' function is for finding roots of a polynomial. AFAIK "characteristic roots" is a somewhat uncommon name for what would usually be referred to as a matix's eigenvalues

```

octave:6> m = [3,5;4,2]
m =

   3   5
   4   2

octave:7> eig(m)
ans =

   7
  -2

octave:8> 

```

Really this whole thread is a perfect example of the [X-Y problem]("http://mywiki.wooledge.org/XyProblem") ...

---

### Post by Kieroneil on 2014-09-19
BTW, I've never heard of the XY Problem but after looking up its definition I agree with you.  I just want to know what the characteristic roots of the matrix [3,5; 4,2] are and it wouldn't be bad to know why but not necessarily needed either.

Thanks for the new info.

---

