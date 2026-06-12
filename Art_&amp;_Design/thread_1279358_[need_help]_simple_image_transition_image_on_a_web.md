---
title: "[need help] simple image transition image on a web page"
date: 2009-09-30
forum: Art &amp; Design
---

### Post by shafin on 2009-09-30
Hi,
I need to get an image transition effect on my web page that'd basically do this.

Get image 1 from server and display.
Then get image 2 from server and display it in place of image 1, with a transition effect like this:

[IMG]http://img190.imageshack.us/img190/308/egistentialism15resized.jpg[/IMG]

to 

[IMG]http://img294.imageshack.us/img294/3028/99264718.jpg[/IMG]

to

[IMG]http://img34.imageshack.us/img34/3395/50781377.jpg[/IMG]

to 

[IMG]http://img34.imageshack.us/img34/2139/72463525.jpg[/IMG]

to 

[IMG]http://img294.imageshack.us/img294/3685/brandlessresizedresized.jpg[/IMG]

with a smooth transition from left to right.


The second image will appear in the place of the first image as parts of it will be revealed from left.
Then the page needs to repeat the effect and show image 1 in place of image 2

What I basically want to show is a real time graph. The image files will be constantly updated in the server so it will appear like a graph with a strip scroll effect, much like this:

[http://www.youtube.com/watch?v=chZqN605Iz4](http://www.youtube.com/watch?v=chZqN605Iz4)

---

### Post by hessiess on 2009-10-01
You could use JavaScript animation like:

[http://www.w3schools.com/JS/js_animation.asp](http://www.w3schools.com/JS/js_animation.asp)

just replace the hover event handler with a timer loop to replace the images:

[http://www.schillmania.com/content/projects/javascript-animation-1/](http://www.schillmania.com/content/projects/javascript-animation-1/)

---

### Post by AJB2K3 on 2009-10-01
Look into Jquery gallery's and there bound to be a pre-made system somewhere.

---

### Post by coldReactive on 2009-10-02
You could also look into APNG.

---

### Post by zyxyellowxyz on 2009-10-02
> **AJB2K3 said:**
> Look into Jquery gallery's and there bound to be a pre-made system somewhere.

jQuery Cycle plugin [http://malsup.com/jquery/cycle/](http://malsup.com/jquery/cycle/)
its easy to customise and I would suggest the fade effect for it.

---

### Post by shafin on 2009-10-02
Thanks a lot for your help. Got it working with some help from sites. Here is the code:
```
<HTML>
<head>

<script type="text/javascript"><!-- 
/*
 _____________________________________
/¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯\
| Another JavaScript from Uncle Jim   |
| Feel free to copy, use and change   |
| this script as long as this part    |
| remains unchanged. You can visit    |
| my website at http://jdstiles.com   |
| for more scripts like this one.     |
| Created: 1998 Updated: 2006         |
\_____________________________________/
 ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
*/
var stopShow = 0;

var SlideShowSpeed = 1500;

var WipeDuration = 3000;



var num=0;




function runSlideShow(){

    //alert(stopShow);
if (stopShow==0){
    if (document.all){
    document.images.PictureBox.style.filter="RevealTrans(duration=WipeDuration,Transition=6)";
    document.images.PictureBox.filters.RevealTrans.Apply();}
    if (num==0)
   {
       document.images.PictureBox.src = 'images/imageA.jpg?' + '?' + (new Date()).getTime();
   }
   if (num==1)
   {
       document.images.PictureBox.src = 'images/imageB.jpg?' + '?' + (new Date()).getTime();
   }
   if (num==2)
   {
       document.images.PictureBox.src = 'images/imageC.jpg?' + '?' + (new Date()).getTime();
   }    

    if (document.all) document.images.PictureBox.filters.RevealTrans.Play();
    num = num + 1;
    if (num > 2) num=0;
    //window.setTimeout('runSlideShow()', SlideShowSpeed);
    }
}

//--></script>


</head>

  <body onload="window.setInterval('runSlideShow()', SlideShowSpeed);">

<IMG alt="" src="images/image1.jpg" id="PictureBox" name="PictureBox" onmouseover="javascript:stopShow=1;" onmouseout="javascript:stopShow=0;">

<br>Monitor
     
  </body>
```Problem with this code is: "revealblend" function works only in IE, got any suggestions on how to make it work in FF?

---

