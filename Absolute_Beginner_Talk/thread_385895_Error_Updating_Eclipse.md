---
title: "Error Updating Eclipse"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-16
I'm trying to update eclipse (so that I can install new plugins) but ... eclipse is encountering an error.
I run help -> Software Updates -> Find and Install -> Search for Updates of the Currently Installed Features -> Data Tools Platform (DTP) ...

Then the WPT update downloads files, the GMF update downloads files, then I get the CDT screen ... when I click OK I get the following error: 

"Data Tools Platform Open Data Access Designer (0.9.1.200609201) requires feature "org.eclipse.emf (2.1.0)", or later version."  

At that point, I can only cancel.  I've also tried installing the PDT plugin which fails for the same reason: "org.eclipse.emf (2.1.0)," or later version required."

Anyone know how I can fix this?  I've tried to get around it several ways, but I'm not quite sure what to do.  Thanks!

---

### Post by Freiburg05 on 2007-03-16
Hi there,

       You say you are trying to update eclipse, but actually you get an error when you try to update plugins, not eclipse itself. Does it mean you have already updated eclipse? 
   
        Anyway, eclipse is asking you to install org.eclipse.emf plugin (eclipse modeling framework). Probably the plugins you are trying to install or update have a dependency with emf. Just install it and it should be fine.

        I see that you are in edgy, so I suppose you have at least eclipse 3.2.1 from repositories. You can download version 3.2.2 from eclipse website (there are no ubuntu oficial packages for this version yet), but I don't think it makes a big difference when it comes to plugins compatibility.


          Hope this helps, bye!

---

### Post by atraeyu on 2007-03-16
So "org.eclipse.emf" refers to a plugin?  Sorry for being a complete noob, but how would I install it?

---

### Post by Freiburg05 on 2007-03-16
Hi! No need to apologize, actually a was a bit asleep in may last post or something because I completely forgot that you can also update eclipse it self from help->software updates. 

To find EMF:     
   
Do help->software updates -> find and install -> search for new features

After that you have to choose the sites. Mark the one called "callisto discovery site".
When the results for the search come you have to go:
     Callisto Discovery site-> models and model development. There it is. 

Cheers!

---

### Post by atraeyu on 2007-03-16
When I follow the instructions like you say ... when I select "models and model development" I get the error "Current Configuration Problems" - if I click "Error Details" there is a list of about 15 different problems.

---

### Post by Freiburg05 on 2007-03-17
mmm I don't know What kind of errors do you get so, I can't help much, but here you have a pair of ideas. 

- If you expand "models and model development" you have 4 packages to install. You only need to select the first three (EMF, SDO, XSD). Maybe this isn't very helpful, but the fourth has some dependency with apache, and besides only the other three are needed for EMF.

- May be you are trying to install EMF 2.3.0. It requires JAVA 1.5.0 to run with eclipse, and it will not run under JAVA 1.4. SO if you are using it as jvm for your eclipse you will need to change it, or install an older version of EMF. This could be a reason for your configuration problems.


    If this doesn't help, try to solve the problems it presents (you can post them here I'll try to help you), if they are dependencies it shouldn't be very troublesome, but who knows..

    Finally, you can find all related to EMF here: [http://www.eclipse.org/modeling/emf/?project=emf]("http://www.eclipse.org/modeling/emf/?project=emf")


    Sorry, I'm not sure if I'll be able to answer until monday, but I'll try. Hope you can solve it.

---

### Post by atraeyu on 2007-03-17
I've got  bunch of homework to do right now, so I don't have time to try your instructions yet ... I'll hopefully get to it before monday though.  Thanks!

---

### Post by gronbaek on 2007-04-24
Hi Atraeyu

Did you ever find a solution to your problem? I have the exact same problem.
I get two different errors... either this:
[IMG]http://gronbaek.net/uploads/eclipse-emf-error.png[/IMG]
or this:
[IMG]http://gronbaek.net/uploads/eclipse-config-error.png[/IMG]

Notice that the first error occurs when I'm actually trying to install the EMF thingy...
And it doesn't matter if i try only selecting some of the sub-updates.

---

### Post by barmazal on 2007-04-24
exact the same problem, moreover when i download whole Callisto lib it fails during install. I think easiest way it to copy PDT over existing Eclipse directory, hopefully it won't mess it even further

---

