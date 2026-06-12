---
title: "code obfuscation"
date: 2008-08-13
forum: Cafe Games
---

### Post by tom66 on 2008-08-13
Post examples of the worst code you have ever seen.

(it must compile/execute)

I would post one but it doesn't work... :(

---

### Post by schauerlich on 2008-08-13
[php]
#!/usr/bin/python

def ballmer() :
    while True :
        print "Developers!"

ballmer()
[/php]

---

### Post by cardinals_fan on 2008-08-13
Perl:```
                $|++;$_L=$K=
       '.';$([199].=$_L.=join 10
  ,<{\\{,\\}}>;            for((@()){
 undef$                      };*::a={a,$K.$
                              T,*$=\$:};$$=Y
                              x(((666)));{$;
                            =$$?join$$,$$,$a
                            {a}:$_L;$;=~tr
                          )Y).);**=
                        \$$$;$*=l1
                       unless 0||
                      defined
                    $*;$*=~#
                    s{$a{a}}
                      $die unless$g;
                          for($S=$*.$}
                             ){($*)=m(^(?:
                               $;)*($a{a}*)
                                \z)x;$==s
                                 $\$;$\$\$$xg
                                  ;;y;Y;;dc;y;Y
                                  ;z;;m.\.*..[$}
                                   =$&  ]}redo
                                 if chop$$
 ;}if(($!                       =$==~y            cccc
 )!=!!$!){$=                -=$=;$__          ++;}$__.=$=
     ;$__=~s"^(.+)([ -8])"\2"and              do{print$1,
         $K;$T.=chop$K}} print                  "$__\n"

```
Before you ask, NO, I don't have that much spare time.  I got it [here]("http://www.perlmonks.org/?showspoiler=703339-1;node_id=1597").

---

### Post by tom66 on 2008-08-13
Here's mine, in PHP. It actually works, but what it does is left as an exercise to the reader.

[php]
<?php

 function a($__, $dP_MTIw, $pd_MTIw) { 

@$__/=(((0550+(1       

          - 
   1)+1)-2)+(1       

          - 
   1)+1); 

@$dP_MTIw/=(bindec('1100100' )+(1       

          - 
   1)+


   0x00); 

@$pd_MTIw/=((((100*1*1*2)-100)-5)+(1       

          - 
   1)+5);


   if($dP_MTIw==(0x0*1*1*1)) {
   $___=$pd['MTQx']=$dp['MTQw']=($pd_MTIw*1*1*(((0377+(1       

          - 
   1)+1)-2)+(1       

          - 
   1)+1)); } else {
   $____=$__*1*1*(bindec('110'


   
   )+(1       

          - 
   1)+


   0x00);
   $dP['MTYx']=floor($____);
   $pd['MTYy']=$pd_MTIw*1*1*(((((1*1*1*2)-1)-5)+(1       

          - 
   1)+5)-$dP_MTIw);
   $_____=$pd_MTIw*1*1*((0x1*1*1*1)-$dP_MTIw*1*1*($____-$dP['MTYx']));
   $pP['MTgw']=$pd_MTIw*1*1*((((01+(1       

          - 
   1)+1)-2)+(1       

          - 
   1)+1)-$dP_MTIw*1*1*((bindec('1' )+(1       

          - 
   1)+


   0x00)-($____-$dP['MTYx'])));


   if($dP['MTYx']==((((0*1*1*2)-0)-5)+(1       

          - 
   1)+5))


    { $Pp['MTgw']=$pd_MTIw; $______=$pP['MTgw']; $pd['MjAz']=$pd['MTYy']; }
   else if($dP['MTYx']==(0x1*1*1*1)) { $Pp['MTgw']=$_____; $______=$pd_MTIw;
$pd['MjAz']=$pd['MTYy']; }
   else if($dP['MTYx']==(((02+(1       

          - 
   1)+1)-2)+(1       

          - 
   1)+1)) { $Pp['MTgw']=$pd['MTYy']; $______=$pd_MTIw; $pd['MjAz']=$pP['MTgw']; }
   else if($dP['MTYx']==(bindec('11' )+(1       

          - 
   1)+


   0x00)) { $Pp['MTgw']=$pd['MTYy']; $______=$_____; $pd['MjAz']=$pd_MTIw; }
   else if($dP['MTYx']==((((4*1*1*2)-4)-5)+(1       

          - 
   1)+5)) { $Pp['MTgw']=$pP['MTgw']; $______=$pd['MTYy']; $pd['MjAz']=$pd_MTIw; }
   else


   


   


   


   { $Pp['MTgw']=$pd_MTIw; $______=$pd['MTYy']; $pd['MjAz']=$_____; }


    $___=$Pp['MTgw']*1*1*(0xff*1*1*1);
   $pd['MTQx']=$______*1*1*(((0377+(1       

          - 
   1)+1)-2)+(1       

          - 
   1)+1);
   $dp['MTQw']=$pd['MjAz']*1*1*(bindec('11111111'
   )+(1       

          - 
   1)+


   0x00); }
   return array(floor($___), floor($pd['MTQx']), floor($dp['MTQw'])); } 
   
?>
[/php]

I wrote a program to obfuscate it, but it required some minor editing after to get it working properly.

---

