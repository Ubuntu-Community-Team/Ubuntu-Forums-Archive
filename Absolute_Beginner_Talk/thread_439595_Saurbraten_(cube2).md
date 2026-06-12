---
title: "Saurbraten (cube2)"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-10
Ive installed it succesfully but when i go to apps-games and click on it i just see a black screen for 4 seconds and then it just quits to my desktop, any suggestions?
Error i got in terminal
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: Mesa GLX Indirect (Mesa project: [www.mesa3d.org](www.mesa3d.org))
Driver: 1.4 (1.5 Mesa 6.5.2)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
Rendering using the OpenGL 1.5 assembly shader path.
COMPILE ERROR (VS:caustic) - (null)
!!ARBvp1.0
    OPTION ARB_position_invariant;
        ATTRIB opos = vertex.position; 

        DP3 result.texcoord[0].x, opos, state.texgen.object.s;
        DP3 result.texcoord[0].y, opos, state.texgen.object.t;
        
    TEMP fogplane;
    MAD fogplane, state.matrix.modelview.row[2], program.env[9].x, program.env[9].yyzw;
    DP4 result.fogcoord, -opos, fogplane;

        END
    SAT&#65533;&#65533;!&#65533;&#65533;&#65533;!&#65533;&#65533; cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP temp, invfresnel, refract, reflect;
    MAD result.color, he, light, temp;
[3`!&#65533;&#65533;`!&#65533;&#65533;
       &#65533;&#65533;
        
    !!ARBfp1.0
   p&#65533;on_hint_fastest;
    


            OPTION ARB_fog_linear;
        ATTRIB htc = fragment.texcoord[0];
        ATTRIB lmtc = fragment.texcoom = fragment.texcoord[1];
        ATTRIB camw = fragment.texcoord[2]; 
            TEMP diffuse, lmc, lmlv, bump, camvts, he, height, light&#65533;  lmtc.zwzw, texture[1], 2D;
            TEX lmlv, lmtc.zwzw, texture[2], 2D;
            MAD lmlv, lmlv, 2, -1;
    
        
        DP3 camvts.w, cam&#65533;(mvts.w;
        MUL camvts.xyz, camvts.w, cam;

        
                ADD he, camvts, lmlv;
                
        DP3 he.w, he, he;
        RSQ he.w, he.w;
        MUL &#65533;&#65533;    

        
            TEX height, htc, texture[4], 2D;
            MAD height.w, height.w, program.&#65533;Gurogram.env[12].y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;xtu&#65533;G&#65533;Dst, dtc, textu &#65533;h&#65533;h&#65533;h&#65533;   &#65533;D&#65533;qragment.texco0&#65533;h&#65533;h&#65533;h&#65533;5      &#65533;&#65533;opmp;
               @&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;SAT&#65533;&#65533;&#65533;mn   MUL lightP&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; TE&#65533;&#65533;&#65533;kl glow, dtc, `&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;fle&#65533;Hij, camw, normp&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;   H&#65533;Dghxw, texture[&#65533;&#65533;&#65533;   &#65533;D&#65533;&#65533;efffuse, light&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;   &#65533;&#65533;`Gcd      

           &#65533;(H&#65533;H&#65533;H&#65533;`G0ab&#65533;8&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9&#65533;#&#65533;&#65533;&#65533;#&#65533;&#65533; 
        !!ARBvp1.0
    OPTION ARB_position_invariant;
        ATTRIB opos = vertex.position; 

        TEMP tc;
        PARAM campos = program.env[0];
        PARAM seconds = program.env[1];
        

        DP4 result.texcoord[0].x, state.matrix.texture.row[0], opos;
        DP4 result.texcoord[0].y, state.matrix.texture.row[1], opos;
        DP4 result.texcoord[0].z, state.matrix.texture.row[2], opos;
        DP4 result.texcoord[0].w, state.matrix.texture.row[3], opos;
        MUL tc, vertex.texcoord[0], 0.1;
        MAD result.texcoord[1], seconds, 0.04, tc;
        MAD result.texcoord[2], seconds, -0.02, tc;
        SUB result.texcoord[3], campos, opos;
        
 
        MOV result.color, vertex.color;

        
    TEMP fogplane;
    MAD fogplane, state.matrix.modelview.row[2], program.env[9].x, program.env[9].yyzw;
    DP4 result.fogcoord, -opos, fogplane;


        END
 &#65533;&#65533;
        
    !!ARBfp1.0
    
    OPTION ARB_precision_hint_fastest;
    


        OPTION ARB_fog_linear;
        TEMP he, light, cam, bump, invfresnel, temp, dudv;

        ATTRIB projtc = fragment.texcoord[0];
        ATTRIB tc1 = fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];
        

        
        DP3 cam.w, camts, camts;
        RSQ cam.w, cam.w;
        MUL cam.xyz, cam.w, camts;

        

        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;

        
    TEMP reflect, refract;

    MAD temp, dudv, 0.4, projtc;
    TXP reflect, temp, texture[0], 2D;
    TXP refract, temp, texture[3], 2D;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1], 2D;
    MAD bump.xyz, bump, 2, -1;


        

        
    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP result.color, invfresnel, refract, reflect;


        END
      ]
88
    spec = $arg2
    distort = $arg3
    combine = $arg4
    shader 1 $arg1 [
        @vpstart
        TEMP tc;
        PARAM campos = program.env[0];
        PARAM seconds = program.env[1];
        @(if $spec [result "PARAM lightpos = program.env[2];"])

        DP4 result.texcoord[0].x, state.matrix.texture.row[0], opos;
        DP4 result.texcoord[0].y, state.matrix.texture.row[1], opos;
        DP4 result.texcoord[0].z, state.matrix.texture.row[2], opos;
        DP4 result.texcoord[0].w, state.matrix.texture.row[3], opos;
        MUL tc, vertex.texcoord[0], 0.1;
        MAD result.texcoord[1], seconds, 0.04, tc;
        MAD result.texcoord[2], seconds, -0.02, tc;
        SUB result.texcoord[3], campos, opos;
        @(if $spec [result "SUB result.texcoord[4], lightpos, opos;"])
 
        MOV result.color, vertex.color;

        @fogcoord

        END
    ] [
        @fpstart
        OPTION ARB_fog_linear;
        TEMP he, light, cam, bump, invfresnel, temp, dudv;

        ATTRIB projtc = fragment.texcoord[0];
        ATTRIB tc1 = fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];
        @(if $spec [result "ATTRIB lightts = fragment.texcoord[4];"])

        @(normalize cam camts)
        @(if $spec [result [
            @(normalize light lightts)
            ADD he, cam, light;
            @(normalize he he)
        ]])

        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;

        @distort

        @(if $spec [result [
            PARAM specfactor = 96;

            DP3_SAT he, he, bump;
            POW he, he.x, specfactor.w;
    
            MUL light, program.env[4], light.w;
            RCP_SAT light, light.x;
            MAD light, light, -program.env[3], program.env[3];
        ]])

        @combine

        END
    ]
2, 1&#65533;
    TEMP caustic, caustic2;
    TEX caustic, fragment.texcoord[0], texture[0], 2D;
    TEX caustic2, fragment.texcoord[0], texture[1], 2D;
    LRP result.color, program.env[0], caustic2, caustic;
 ] [
 a&#65533;!&#65533;&#65533;&#65533;!&#65533;&#65533;art
        OPTION ARB_fog_linear;
        @arg2
        END
    ]
&#65533;GX!&#65533;&#65533;`combineampl er!reflectivity&#65533;X!&#65533;&#65533; &#65533;  
            TEX scaled, fragment.texcoord[1], texture[1], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[2], texture[2], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[3], texture[3], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[4], texture[4], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[5], texture[5], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[6], texture[6], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
        &#65533;&#65533;
        
    !!ARBfp1.0
    
    OPTION ARB_precision_hint_fastest;
    


        OPTION ARB_fog_linear;
        TEMP he, light, cam, bump, invfresnel, temp, dudv;

        ATTRIB projtc = fragment.texcoord[0];
        ATTRIB tc1 = fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];
        ATTRIB lightts = fragment.texcoord[4];

        
        DP3 cam.w, camts, camts;
        RSQ cam.w, cam.w;
        MUL cam.xyz, cam.w, camts;

        
            
        DP3 light.w, lightts, lightts;
        RSQ light.w, light.w;
        MUL light.xyz, light.w, lightts;

            ADD he, cam, light;
            
        DP3 he.w, he, he;
        RSQ he.w, he.w;
        MUL he.xyz, he.w, he;

        

        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;

        
    TEMP reflect, refract;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1], 2D;
    MAD bump.xyz, bump, 2, -1;
    TEX dudv, temp, texture[2], 2D;
    MAD dudv.xy, dudv, 2, -1;

    RCP temp.w, projtc.w;
    MUL temp.xyz, projtc, temp.wwww; 
    MAD temp.xy, dudv, 0.01, temp;

    TEX reflect, temp, texture[0], 2D;
    TEX refract, temp, texture[3], 2D;


        
            PARAM specfactor = 96;

            DP3_SAT he, he, bump;
            POW he, he.x, specfactor.w;
    
            MUL light, program.env[4], light.w;
            RCP_SAT light, light.x;
            MAD light, light, -program.env[3], program.env[3];
        

        
    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP temp, invfresnel, refract, reflect;
    MAD result.color, he, light, temp;


        END
    y&#65533;Segmentation fault (core dumped)

---

### Post by crispy_420 on 2007-05-10
For starters it looks like a video card issue. That may be the root of your problem. What video card do you have and is it setup for OpenGL rendering? To me it looks as though the answer to number to is no. 

To solve your issue, post what video card and the relevant part of your xorg.

---

### Post by mojo123 on 2007-05-10
How do i figure out my video card?

---

### Post by autocrosser on 2007-05-10
A couple of ways--
1> Menu>System Tools>Sysinfo (if you have it installed)
2> Menu>System>Administration>Stysem Log & look qat the current Xorg.0.log--the log will tell you almost everything you want to know about you current X syste.

---

### Post by mojo123 on 2007-05-12
[http://paste.uni.cc/15394](http://paste.uni.cc/15394)
THis is my xorg.0.log

---

### Post by autocrosser on 2007-05-12
So it looks like you are using a laptop or motherboard video. In any case, I don't believe you have enough video memory to run the program. If you are using a desktop, I would invest in a video card---If it is a laptop, I don't know--some of the others in the games forum use laptops (I don't) & would be able to give you tips.

---

### Post by mojo123 on 2007-05-13
i really cant handle it, this is a entertainment pc!

---

