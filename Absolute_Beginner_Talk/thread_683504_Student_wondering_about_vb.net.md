---
title: "Student wondering about vb.net"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-31
Hey all,

I'm looking to take some CIS classes. Just to be sure, I sent an email to the department at the college to ask if I could make it with just a Linux OS installed on my machine. Here is the relevant portion of the response I received:

"If he installs or has installed a Microsoft operating system on his Linux machine and then buys Microsoft Office for $60 (deal is only good for students) and installs that, he could then dual-boot and go through the program without a problem.

With just Linux he could take the UNIX classes and maybe some others, but he definitely couldn't take VB.Net classes. He might be able to take C++ and Java classes. He couldn't take my version of [a particular class] because it requires having VBA."

I don't know specifically what he's talking about, but I want so badly for him to be wrong! Do I really have to buy a copy of MS Office?! Being the ignoramus that I am, I installed Mono and MonoDevelop on my system. Will that give me what I need?

What I want, ultimately, is to be able to succeed in these classes entirely outside of a Windows environment; also, I want to be able to tell this prof exactly how I intend to do that. That's where I need your help: Someone please tell me I can make this happen without M$!

Thank you!

EDIT: Just for the record, I know I'm covered in almost all languages if I use any of the multitude of IDEs out there (personally, I like Geany). I'm really concerned about this .NET stuff (VB.NET, VBA, etc) - something with which I'm entirely unfamiliar.

---

### Post by hyper_ch on 2008-01-31
Depending on the school you are in they could be participants of the MSDNAA and you might get an Office copy there:  [http://www.msdnaa.net/search/schoolsearch.aspx](http://www.msdnaa.net/search/schoolsearch.aspx)

---

### Post by Rhubarb on 2008-01-31
Mono may work for you, also try out: [http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)
It's very similar to vb apparently.

---

### Post by doctorbighands on 2008-01-31
> **hyper_ch said:**
> Depending on the school you are in they could be participants of the MSDNAA and you might get an Office copy there:  [http://www.msdnaa.net/search/schoolsearch.aspx](http://www.msdnaa.net/search/schoolsearch.aspx)

Do I take this to mean that I won't survive without Windows?

---

### Post by hyper_ch on 2008-01-31
You can take this whatever way you want.

---

### Post by jaytek13 on 2008-01-31
> **doctorbighands said:**
> Do I take this to mean that I won't survive without Windows?

I'm not sure what they're saying they require office for, unless you're taking a word processing or excel or access class or something. Otherwise, just for documents/flow charts open office is perfectly fine.


As far as developing vb.net apps with mono, it should technically work, with these exceptions

    *  Default instances (this is planned to be done soon)
    * The support for late-binding, Option Strict Off / Option Explicit Off is very limited (this is much more work and will come gradually)
    * XML comments (no plans for this for the moment) 

Information taken from this page: [http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support)  . You'll probably want to take a look over that.

But, obviously you can see the people in the beginner forum aren't going to be very helpful with programming topics. You might consider reposting the question about vb.net in the programming subforum rather than here.

---

### Post by doctorbighands on 2008-01-31
> **jaytek13 said:**
> I'm not sure what they're saying they require office for, unless you're taking a word processing or excel or access class or something. Otherwise, just for documents/flow charts open office is perfectly fine.


As far as developing vb.net apps with mono, it should technically work, with these exceptions

    *  Default instances (this is planned to be done soon)
    * The support for late-binding, Option Strict Off / Option Explicit Off is very limited (this is much more work and will come gradually)
    * XML comments (no plans for this for the moment) 

Information taken from this page: [http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support)  . You'll probably want to take a look over that.

But, obviously you can see the people in the beginner forum aren't going to be very helpful with programming topics. You might consider reposting the question about vb.net in the programming subforum rather than here.

Excellent. Thank you very much for this.

---

### Post by OoooMatron on 2008-01-31
I run XP in virtual box with Visual Studio inside. Using seamless windows it's perfect.

---

