---
title: "Compiling software library"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Bingo Jesus on 2007-09-19
I am busy working on a project in C and have been given [this]("http://www.maths.cam.ac.uk/undergrad/catam//ccatsl/") library to work with. I only require it for the graph plotting features as I have done everything else required using standard libraries. 

When I try to compile it I get an error:
```

xxxx@xxxx-laptop:~/Desktop$ make
gcc  -c ccatslnum.c -o ccatslnum.o -I.
ccatslnum.c: In function ‘_Set_error’:
ccatslnum.c:75: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccatslnum.c: In function ‘_setmatherror’:
ccatslnum.c:253: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccatslnum.c: In function ‘Rkf45CL’:
ccatslnum.c:1783: warning: incompatible implicit declaration of built-in function ‘memcpy’
ccatslnum.c: In function ‘_errormatrix’:
ccatslnum.c:2263: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccatslnum.c: In function ‘_local_copy’:
ccatslnum.c:2320: warning: incompatible implicit declaration of built-in function ‘memmove’
ccatslnum.c: In function ‘_strdelete’:
ccatslnum.c:3688: warning: incompatible implicit declaration of built-in function ‘strlen’
ccatslnum.c: In function ‘_strinsert’:
ccatslnum.c:3708: warning: incompatible implicit declaration of built-in function ‘strlen’
ccatslnum.c:3712: warning: incompatible implicit declaration of built-in function ‘strcpy’
ccatslnum.c: In function ‘_strpos2’:
ccatslnum.c:3764: warning: incompatible implicit declaration of built-in function ‘strlen’
```

Am I doing this correctly? Should I give up on this library and just export my results as a comma separated table instead and plot elsewhere?

Many thanks,
Bingo Jesus

---

### Post by hyper_ch on 2007-09-19
this is a windows program.

---

### Post by justleen on 2007-09-19
> **hyper_ch said:**
> this is a windows program.

at the bottom of the site, theres a link to the source (ofr other OS'es)

perhaps try and compile that library first?
(if you havent done so..)

---

### Post by Bingo Jesus on 2007-09-19
> **justleen said:**
> at the bottom of the site, theres a link to the source (ofr other OS'es)

perhaps try and compile that library first?
(if you havent done so..)

Yeah, that's the source which gives me the error when compiling.

---

### Post by jamvegan on 2007-09-19
Well, there are no actual errors there, just warnings.  So it probably did produce ccatslnum.o.  Have you tried using it?

---

### Post by Bingo Jesus on 2007-09-19
> **jamvegan said:**
> Well, there are no actual errors there, just warnings.  So it probably did produce ccatslnum.o.  Have you tried using it?

I got rid of the errors by adding an #include <strings.h>, I'm now not sure what to do with the generated ccatslnum.o. How do I include it in my programs?

---

### Post by jamvegan on 2007-09-19
If you are using gcc, take a look at [An Introduction to GCC]("http://www.network-theory.co.uk/docs/gccintro/gccintro_12.html").  It's a very clear, concise book that's available in its entirety online for free.  The page that I linked, and the two pages following it (they're all very short pages) should answer your question.

---

### Post by Bingo Jesus on 2007-09-19
> **jamvegan said:**
> If you are using gcc, take a look at [An Introduction to GCC]("http://www.network-theory.co.uk/docs/gccintro/gccintro_12.html").  It's a very clear, concise book that's available in its entirety online for free.  The page that I linked, and the two pages following it (they're all very short pages) should answer your question.

Super, thank you.

---

