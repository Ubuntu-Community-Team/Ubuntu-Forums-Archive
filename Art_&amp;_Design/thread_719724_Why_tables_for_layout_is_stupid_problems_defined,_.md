---
title: "Why tables for layout is stupid: problems defined, solutions offered"
date: 2008-03-09
forum: Art &amp; Design
---

### Post by st0n3cutt3r on 2008-03-09
The problem with using tables:
[LIST]
[*]mixes presentational data in with your content. 
[*]This makes the file sizes of your pages unnecessarily large, as users must download this presentational data for each page they visit.
[*]Bandwidth ain't free.
[*]This makes redesigns of existing sites and content extremely labor intensive (and expensive).
[*]It also makes it extremely hard (and expensive) to maintain visual consistency throughout a site.
[*]**Table-based pages are also much less accessible to users with disabilities and viewers using cell phones and PDAs to access the Web.**
[/LIST]

_[http://www.hotdesign.com/seybold/everything.html]("http://www.hotdesign.com/seybold/everything.html")_

Read it, Learn it, Do it.
______________________________

Other thoughts: We really need a Web Design/Development forum with a link to this site on a sticky post, and where people can come for help to break bad layout habits.

---

### Post by AJB2K3 on 2008-03-09
> **st0n3cutt3r said:**
> The problem with using tables:
[LIST]
[*]mixes presentational data in with your content. 
[*]This makes the file sizes of your pages unnecessarily large, as users must download this presentational data for each page they visit.
[*]Bandwidth ain't free.
[*]This makes redesigns of existing sites and content extremely labor intensive (and expensive).
[*]It also makes it extremely hard (and expensive) to maintain visual consistency throughout a site.
[*]**Table-based pages are also much less accessible to users with disabilities and viewers using cell phones and PDAs to access the Web.**
[/LIST]

_[http://www.hotdesign.com/seybold/everything.html]("http://www.hotdesign.com/seybold/everything.html")_

Read it, Learn it, Do it.
______________________________

Other thoughts: We really need a Web Design/Development forum with a link to this site on a sticky post, and where people can come for help to break bad layout habits.

Tables are only made for display of data in a tabloid form.
Anyone who uses tables for layout are lazy $£"^* and don't know jack about proper web design

---

### Post by argraff on 2008-03-12
> **AJB2K3 said:**
> Tables are only made for display of data in a tabloid form.
Anyone who uses tables for layout are lazy $£"^* and don't know jack about proper web design

Or new to the concept and haven't discovered CSS yet...I am a convert myself! :) (in my defense, it's been several years now.)

---

### Post by argraff on 2008-03-12
> **st0n3cutt3r said:**
> 

_[http://www.hotdesign.com/seybold/everything.html]("http://www.hotdesign.com/seybold/everything.html")_

Read it, Learn it, Do it.
______________________________

Other thoughts: We really need a Web Design/Development forum with a link to this site on a sticky post, and where people can come for help to break bad layout habits.

Oh! Sadness st0n3cutt3r! This is in FF 2.0.0.12. Love the artwork though - very nice!

---

### Post by st0n3cutt3r on 2008-03-12
it's supposed to do that! it's an overlaying javascript menu. 
You're going to have to do better than that if you want to try to prove that there's some reason to use tables over clean valid code....  [QUOTE=AJB2K3]Anyone who uses tables for layout are lazy $£"^* and don't know jack about proper web design[/QUOTE]

---

### Post by bmeyer on 2008-03-12
I agree with this to a certain degree.  CSS design is certainly efficient, but it's been my experience that complex CSS-only layouts don't always render similarly enough in different browsers to be usable.  I've used tables for structure with CSS for all the styling a lot for clients and it usually works out well.  If you do it right, the code is still very efficient and accessible and seems to currently be the most cross-browser compliant solution -- for the time being of course.

---

### Post by st0n3cutt3r on 2008-03-12
One of the big issues with tables, despite the fact that you can get light-weight pages by putting all of your styling in CSS, is that they are usually completely unusable by anything but regular screens.  Largely inaccessible to small screen browsers (like on mobile phones and PDAs), and completely inaccessible to people using screen readers and other accessibility devices.

It's great that you can set up your page to look EXACTLY how you want it to in a table, but who (aside from developers) ever looks at the page in more than one browser to know that there's a difference?

Yeah, it might be off by a couple of pixels on IE or Netscape or something like that, but "big deal"  it's really not significant relative to what you are doing to lock other people out of your site by putting your content in a table.

---

### Post by Merk42 on 2008-03-13
[So close to compliancy](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.hotdesign.com%2Fseybold%2Feverything.html&charset=%28detect+automatically%29&doctype=Inline&group=0)

---

### Post by AJB2K3 on 2008-03-14
> **st0n3cutt3r said:**
> it's supposed to do that! it's an overlaying javascript menu. 
You're going to have to do better than that if you want to try to prove that there's some reason to use tables over clean valid code....

I wasn't trying I was just ranting.
Using table for webdesign is like using a motor bike to move furniture.


> **Merk42 said:**
> [So close to compliancy](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.hotdesign.com%2Fseybold%2Feverything.html&charset=%28detect+automatically%29&doctype=Inline&group=0)

??

Dear lord that page's css in a nightmare.
I think he should move the css to a seperate document so he can see the problem he has.

---

### Post by st0n3cutt3r on 2008-03-14
that page is an 'everything' page. It was created so that they could send the entire file as one link/page to people w/out internet access, or for easy referral.  It explains somewhere on the page.  I remember reading it after checking their code and nearly having a fit after seeing all of the internal CSS on my first visit to the site.

yes, looks like they accidentally added a space before the "...   I think we can forgive them one error (if not for not validating).

---

### Post by st0n3cutt3r on 2008-03-22
more people need to read this!

---

