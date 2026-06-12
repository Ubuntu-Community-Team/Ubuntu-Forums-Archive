---
title: "TItle bar buttons in a restricted environment"
date: 2007-05-23
forum: Assistive Technology &amp; Accessibility
---

### Post by deadowl on 2007-05-23
I have recently been discussing on the GNOME Usability List about the ability to reorder buttons on the title bar. My argument is that there are several use cases for reordering the buttons.

1.) Reordering to match the environment from which one migrated from.
2.) Reordering for the purpose of putting spacers between buttons so that none are accidentally pressed.
3.) Reordering to improve the experience in a restricted environment.

Case one can be had for users migrating from OS/X.
Case two is a similar change from what Windows did with Vista for the reasoning of adding a spacer between min/max and close.
I certainly use KDE specifically for case three.

On my laptop, I have a touchpad. A touch pad is more inherently restrictive than a mouse. As a result, I like grouping the functionality that the window buttons give me. I put them on the left side of the title bar and stack shaded windows so I can navigate and work between windows more easily.

GNOME has this ability. However, it is not included in the window settings, and even more of a problem, one has to edit a text file in order for it to work. No casual user would ever guess to do so without being told it exists.

I have received responses such as the following:

On May 23, 2007, at 9:03 AM, <name redacted> wrote:
>
> On Tuesday 22 May 2007 11:18:22 Mike Burns wrote:
> ...
>> In gconf, apps/metacity/general/button_layout. For example,
>> "menu,minimize,maximize,close:" will put everything on the left side
>> of the titlebar.
>
> So the ability both exists and is useful? The question remains, why is 
> it so hidden?
> ...

Because the ease of doing anything in an interface should be 
proportional to how many people want to do it, how often they want to 
do it, how urgently they want to do it, and the average benefit of 
doing it.

With rearranging title bar buttons, hardly anyone wants to, those who 
do typically do it only once, it's never urgent, and the benefit is not 
great. Given that, it's remarkable that it doesn't even require 
recompiling.

(I've rearranged them for myself, because having the close button right 
next to the others is stupid. But I think that's an argument for having 
a better default arrangement, not for making the customization easier.)

Cheers
-- 


_______________________________________________
Usability mailing list
[email]Usability@gnome.org[/email]
[http://mail.gnome.org/mailman/listinfo/usability](http://mail.gnome.org/mailman/listinfo/usability)


On May 23, 2007, at 1:48 PM, <name redacted> wrote:
> ...
> On Tuesday 22 May 2007 20:45:41 Matthew Paul Thomas wrote:
>>
>> Because the ease of doing anything in an interface should be
>> proportional to how many people want to do it, how often they want to
>> do it, how urgently they want to do it, and the average benefit of
>> doing it.
>>
>> With rearranging title bar buttons, hardly anyone wants to, those who
>> do typically do it only once, it's never urgent, and the benefit is 
>> not great. Given that, it's remarkable that it doesn't even require
>> recompiling.
>
> I've already explained why the benefit is great for me.

Yes, you have, which is why you're here. Meanwhile, the vast majority 
of other Gnome users are getting actual work done.

On a constructive note, if you are now motivated to even the effort 
slope a bit by developing your own TweakUI-like utility for options 
like that, I'm sure others would be interested.

> It helps me perform *organizational strategies in a restricted 
> environment. The ease of doing so is one of the biggest reasons I 
> prefer KDE to GNOME.

And conversely, the lack of such prominent geekery is part of the 
reason revenue-seeking Linux distributors prefer Gnome to KDE.

> ...
> There is one major problem with what you are saying: Apart from the 
> fact people rarely change any preferences, if specific functionality 
> is not available via settings, users often expect that it doesn't 
> exist.

Most functions of *any* graphical program aren't available via its 
settings.

> If I asked my mom to perform the task of moving the buttons from the 
> top-right of the window to the top-left of the window, she wouldn't 
> know how to do it. She would probably spend a half hour in the 
> preferences menu bar looking for things that might be able to do it.
> ...

I admire your mother's tenacity, but for goodness sake, don't you and 
she both have more interesting things to do? :-)

-- 

_______________________________________________



Usability mailing list
[email]Usability@gnome.org[/email]
[http://mail.gnome.org/mailman/listinfo/usability](http://mail.gnome.org/mailman/listinfo/usability)


I'm sorry, that came out badly.

What I meant was, the vast majority of Gnome users aren't in the same 
situation as you, preferring one button order in one environment and 
another button order in another environment. So if the option was more 
prominent, the extra confusion to them would outweigh the extra 
usefulness to you. That's an unfortunate equation, but it exists.

So if you want to help Gnome, and also make it tolerable for your own 
use, it would be great if you could develop (or pay or otherwise 
persuade someone else to develop) a separate installable utility for 
quicker configuration of options like that. It's something Gnome 
contributors have often talked about in the past, but as far as I know 
nobody has done it.

Cheers
-- 


_______________________________________________
Usability mailing list
[email]Usability@gnome.org[/email]
[http://mail.gnome.org/mailman/listinfo/usability](http://mail.gnome.org/mailman/listinfo/usability)


So essentially, what I'm being told is:

1.) The number of users that would utilize a feature should be proportional to the ease of use of the feature. (Okay, so what if we made it so that blind users had to program their own screenreaders since they are such a small minority?)

2.) I'm a hypocrite because I've actually modified my button ordering. I wish I had to recompile everything just to do that.

3.) Put your code where your mouth is, because I'm sure developers would actually want to see this implemented. (This I don't get because the guy has already argued that it should be hard-coded)


How does Ubuntu choose a desktop manager with this kind of attitude on usability as its default desktop manager? I understand that consistency is much better with GNOME than some other window managers, but there's obviously something wrong.

---

### Post by Jussi Kukkonen on 2007-05-23
> So essentially, what I'm being told is:

1.) The number of users that would utilize a feature should be proportional to the ease of use of the feature. (Okay, so what if we made it so that blind users had to program their own screenreaders since they are such a small minority?)

2.) I'm a hypocrite because I've actually modified my button ordering. I wish I had to recompile everything just to do that.

3.) Put your code where your mouth is, because I'm sure developers would actually want to see this implemented. (This I don't get because the guy has already argued that it should be hard-coded)
No, you are being told that in their opinion the vast majority of users do not need this functionality and it's not critical to even those who would like it, and that this is reason enough for metacity developers to not include the option...

Case in point: you asked a question about screenreaders. That case is clearly handled by the second and last points in this list you were given: 
[I]"Because the ease of doing anything in an interface should be
proportional to how many people want to do it, [B]how often they want to
do it[/B], how urgently they want to do it, and [B]the average benefit of
doing it.[/B]"[/I]

If you don't like it, you don't have to go to KDE: just install another window manager that has more options (openbox comes to mind).

> 
How does Ubuntu choose a desktop manager with this kind of attitude on usability as its default desktop manager? 
No offence, but they just disagreed with you.

---

### Post by deadowl on 2007-05-23
The average benefit when working with a touchpad is about 5 seconds of work per window (dependant on size) while multitasking. There are also different benefits among different use cases depending on how the user interacts with the system. This feature is supported, just hidden. I don't believe it should be hidden because of the inherent benefits. So yes, the average benefit does exist and is certainly high enough to justify its being less hidden.

I also could imagine a similar situation for people using screenreaders in the face of redundant text (which is what I hear is one of the more annoying things that can happen for a blind user). It's certainly not critical, but it would save a lot of time on behalf of the user.

---

