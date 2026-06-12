---
title: "GIMP Normalmap Plugin Woes"
date: 2007-08-16
forum: Art &amp; Design
---

### Post by Megatog615 on 2007-08-16
On my laptop(which has a pretty old NVIDIA Geforce2 Go), I can run and use the Normalmap plugin just fine. However, there are a few issues. I cannot change anything besides the diffuse map in the 3D preview. I figure this is due to some lack of support from the video card. Is there any way I can run it in software mode(using mesa or something), so I can get all the features? It will probably run very slow, but it's just a single texture I'm viewing and it shouldn't be a problem.

---

### Post by fktt on 2007-08-16
where do you have to but the normalmap plugin in the gimp, anyway, have tryed and i didnt get it even working :(

---

### Post by Sindwiller on 2007-08-16
> **fktt said:**
> where do you have to but the normalmap plugin in the gimp, anyway, have tryed and i didnt get it even working :(

You need to compile it yourself. It's pretty easy...

```
tar -xjf gimp-normalmap-1.2.1.tar.bz2
cd gimp-normalmap-1.2.1
make
sudo make install
```

And here's a little HowTo for good normalmaps I wrote on the Nexuiz forums... [http://alientrap.org/forum/viewtopic.php?p=16725&sid=626ec56e8460557618717b8ea9fc5d8c#16725](http://alientrap.org/forum/viewtopic.php?p=16725&sid=626ec56e8460557618717b8ea9fc5d8c#16725)

> I cannot change anything besides the diffuse map in the 3D preview.

Is "Specular Lighting" ticked? Have you selected a correct specularmap?

---

### Post by Megatog615 on 2007-08-16
I can't. I think my video card can't support things like that, which is why I'm asking for a way to do it through mesaGL.

---

### Post by fktt on 2007-08-19
> **Sindwiller said:**
> You need to compile it yourself. It's pretty easy...

```
tar -xjf gimp-normalmap-1.2.1.tar.bz2
cd gimp-normalmap-1.2.1
make
sudo make install
``` aha, thanks :)

---

### Post by fktt on 2007-09-12
ok.. so i finally got around to checking out the nor-map-plugin's compile/make, and this is what i get:

***[edit: changed the error code, got some things fixed on my own, but problems still exist, and now i really cant get my tiny head around it..]***

```

gcc -c -O3 -Wall `pkg-config --cflags gtk+-2.0 gtkglext-1.0 gimp-2.0` normalmap.c
normalmap.c: In function &#8216;normalmap_dialog&#8217;:
normalmap.c:1331: warning: missing sentinel in function call
gcc -c -O3 -Wall `pkg-config --cflags gtk+-2.0 gtkglext-1.0 gimp-2.0` preview3d.c
preview3d.c:27:21: error: GL/glew.h: No such file or directory
preview3d.c:89: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;diffuse_tex&#8217;
preview3d.c:90: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;gloss_tex&#8217;
preview3d.c:91: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;normal_tex&#8217;
preview3d.c:92: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;white_tex&#8217;
preview3d.c:100: error: expected specifier-qualifier-list before &#8216;GLuint&#8217;
preview3d.c:103: warning: excess elements in struct initializer
preview3d.c:103: warning: (near initialization for &#8216;object_info[0]&#8217;)
preview3d.c:104: warning: excess elements in struct initializer
preview3d.c:104: warning: (near initialization for &#8216;object_info[1]&#8217;)
preview3d.c:105: warning: excess elements in struct initializer
preview3d.c:105: warning: (near initialization for &#8216;object_info[2]&#8217;)
preview3d.c:106: warning: excess elements in struct initializer
preview3d.c:106: warning: (near initialization for &#8216;object_info[3]&#8217;)
preview3d.c:107: warning: excess elements in struct initializer
preview3d.c:107: warning: (near initialization for &#8216;object_info[4]&#8217;)
preview3d.c:121: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;programs&#8217;
preview3d.c: In function &#8216;init&#8217;:
preview3d.c:592: warning: implicit declaration of function &#8216;glewInit&#8217;
preview3d.c:593: error: &#8216;GLEW_OK&#8217; undeclared (first use in this function)
preview3d.c:593: error: (Each undeclared identifier is reported only once
preview3d.c:593: error: for each function it appears in.)
preview3d.c:595: warning: implicit declaration of function &#8216;glewGetErrorString&#8217;
preview3d.c:595: warning: passing argument 3 of &#8216;g_log&#8217; makes pointer from integer without a cast
preview3d.c:599: warning: implicit declaration of function &#8216;glClearColor&#8217;
preview3d.c:600: warning: implicit declaration of function &#8216;glDepthFunc&#8217;
preview3d.c:600: error: &#8216;GL_LEQUAL&#8217; undeclared (first use in this function)
preview3d.c:601: warning: implicit declaration of function &#8216;glEnable&#8217;
preview3d.c:601: error: &#8216;GL_DEPTH_TEST&#8217; undeclared (first use in this function)
preview3d.c:603: warning: implicit declaration of function &#8216;glLineWidth&#8217;
preview3d.c:607: error: &#8216;GLEW_ARB_multitexture&#8217; undeclared (first use in this function)
preview3d.c:613: error: &#8216;GLEW_ARB_texture_env_combine&#8217; undeclared (first use in this function)
preview3d.c:619: error: &#8216;GLEW_ARB_texture_env_dot3&#8217; undeclared (first use in this function)
preview3d.c:627: warning: implicit declaration of function &#8216;glGenTextures&#8217;
preview3d.c:627: error: &#8216;diffuse_tex&#8217; undeclared (first use in this function)
preview3d.c:628: error: &#8216;gloss_tex&#8217; undeclared (first use in this function)
preview3d.c:629: error: &#8216;normal_tex&#8217; undeclared (first use in this function)
preview3d.c:630: error: &#8216;white_tex&#8217; undeclared (first use in this function)
preview3d.c:632: warning: implicit declaration of function &#8216;glGetIntegerv&#8217;
preview3d.c:632: error: &#8216;GL_MAX_TEXTURE_UNITS&#8217; undeclared (first use in this function)
preview3d.c:634: warning: implicit declaration of function &#8216;glActiveTexture&#8217;
preview3d.c:634: error: &#8216;GL_TEXTURE0&#8217; undeclared (first use in this function)
preview3d.c:635: error: &#8216;GL_TEXTURE_2D&#8217; undeclared (first use in this function)
preview3d.c:636: warning: implicit declaration of function &#8216;glTexEnvi&#8217;
preview3d.c:636: error: &#8216;GL_TEXTURE_ENV&#8217; undeclared (first use in this function)
preview3d.c:636: error: &#8216;GL_TEXTURE_ENV_MODE&#8217; undeclared (first use in this function)
preview3d.c:636: error: &#8216;GL_COMBINE&#8217; undeclared (first use in this function)
preview3d.c:637: error: &#8216;GL_COMBINE_RGB&#8217; undeclared (first use in this function)
preview3d.c:637: error: &#8216;GL_DOT3_RGB&#8217; undeclared (first use in this function)
preview3d.c:638: error: &#8216;GL_SOURCE0_RGB&#8217; undeclared (first use in this function)
preview3d.c:638: error: &#8216;GL_PRIMARY_COLOR&#8217; undeclared (first use in this function)
preview3d.c:639: error: &#8216;GL_OPERAND0_RGB&#8217; undeclared (first use in this function)
preview3d.c:639: error: &#8216;GL_SRC_COLOR&#8217; undeclared (first use in this function)
preview3d.c:640: error: &#8216;GL_SOURCE1_RGB&#8217; undeclared (first use in this function)
preview3d.c:640: error: &#8216;GL_TEXTURE&#8217; undeclared (first use in this function)
preview3d.c:641: error: &#8216;GL_OPERAND1_RGB&#8217; undeclared (first use in this function)
preview3d.c:643: error: &#8216;GL_TEXTURE1&#8217; undeclared (first use in this function)
preview3d.c:646: error: &#8216;GL_MODULATE&#8217; undeclared (first use in this function)
preview3d.c:647: error: &#8216;GL_PREVIOUS&#8217; undeclared (first use in this function)
preview3d.c:652: warning: implicit declaration of function &#8216;glBindTexture&#8217;
preview3d.c:653: warning: implicit declaration of function &#8216;glTexParameteri&#8217;
preview3d.c:653: error: &#8216;GL_TEXTURE_WRAP_S&#8217; undeclared (first use in this function)
preview3d.c:653: error: &#8216;GL_CLAMP_TO_EDGE&#8217; undeclared (first use in this function)
preview3d.c:654: error: &#8216;GL_TEXTURE_WRAP_T&#8217; undeclared (first use in this function)
preview3d.c:655: error: &#8216;GL_TEXTURE_MAG_FILTER&#8217; undeclared (first use in this function)
preview3d.c:655: error: &#8216;GL_NEAREST&#8217; undeclared (first use in this function)
preview3d.c:656: error: &#8216;GL_TEXTURE_MIN_FILTER&#8217; undeclared (first use in this function)
preview3d.c:657: warning: implicit declaration of function &#8216;glTexImage2D&#8217;
preview3d.c:657: error: &#8216;GL_LUMINANCE&#8217; undeclared (first use in this function)
preview3d.c:658: error: &#8216;GL_UNSIGNED_BYTE&#8217; undeclared (first use in this function)
preview3d.c:662: error: &#8216;GL_TEXTURE2&#8217; undeclared (first use in this function)
preview3d.c:667: error: &#8216;GLEW_ARB_shader_objects&#8217; undeclared (first use in this function)
preview3d.c:667: error: &#8216;GLEW_ARB_vertex_shader&#8217; undeclared (first use in this function)
preview3d.c:668: error: &#8216;GLEW_ARB_fragment_shader&#8217; undeclared (first use in this function)
preview3d.c:669: error: &#8216;GLEW_ARB_texture_non_power_of_two&#8217; undeclared (first use in this function)
preview3d.c:670: error: &#8216;GLEW_SGIS_generate_mipmap&#8217; undeclared (first use in this function)
preview3d.c:671: error: &#8216;GLEW_EXT_texture_filter_anisotropic&#8217; undeclared (first use in this function)
preview3d.c:675: error: &#8216;GLhandleARB&#8217; undeclared (first use in this function)
preview3d.c:675: error: expected &#8216;;&#8217; before &#8216;prog&#8217;
preview3d.c:685: error: &#8216;GLEW_ARB_fragment_program&#8217; undeclared (first use in this function)
preview3d.c:687: warning: implicit declaration of function &#8216;glBindProgramARB&#8217;
preview3d.c:687: error: &#8216;GL_FRAGMENT_PROGRAM_ARB&#8217; undeclared (first use in this function)
preview3d.c:688: warning: implicit declaration of function &#8216;glGetProgramivARB&#8217;
preview3d.c:689: error: &#8216;GL_MAX_PROGRAM_NATIVE_ALU_INSTRUCTIONS_ARB&#8217; undeclared (first use in this function)
preview3d.c:692: error: &#8216;GL_MAX_PROGRAM_NATIVE_TEX_INDIRECTIONS_ARB&#8217; undeclared (first use in this function)
preview3d.c:697: error: &#8216;vert_shader&#8217; undeclared (first use in this function)
preview3d.c:697: warning: implicit declaration of function &#8216;glCreateShaderObjectARB&#8217;
preview3d.c:697: error: &#8216;GL_VERTEX_SHADER_ARB&#8217; undeclared (first use in this function)
preview3d.c:698: warning: implicit declaration of function &#8216;glShaderSourceARB&#8217;
preview3d.c:699: warning: implicit declaration of function &#8216;glCompileShaderARB&#8217;
preview3d.c:700: warning: implicit declaration of function &#8216;glGetObjectParameterivARB&#8217;
preview3d.c:700: error: &#8216;GL_OBJECT_COMPILE_STATUS_ARB&#8217; undeclared (first use in this function)
preview3d.c:703: error: &#8216;GL_OBJECT_INFO_LOG_LENGTH_ARB&#8217; undeclared (first use in this function)
preview3d.c:705: warning: implicit declaration of function &#8216;glGetInfoLogARB&#8217;
preview3d.c:710: error: &#8216;prog&#8217; undeclared (first use in this function)
preview3d.c:710: warning: implicit declaration of function &#8216;glCreateProgramObjectARB&#8217;
preview3d.c:711: warning: implicit declaration of function &#8216;glAttachObjectARB&#8217;
preview3d.c:713: error: &#8216;frag_shader&#8217; undeclared (first use in this function)
preview3d.c:713: error: &#8216;GL_FRAGMENT_SHADER_ARB&#8217; undeclared (first use in this function)
preview3d.c:727: warning: implicit declaration of function &#8216;glDeleteObjectARB&#8217;
preview3d.c:734: warning: implicit declaration of function &#8216;glLinkProgramARB&#8217;
preview3d.c:735: error: &#8216;GL_OBJECT_LINK_STATUS_ARB&#8217; undeclared (first use in this function)
preview3d.c:749: error: &#8216;programs&#8217; undeclared (first use in this function)
preview3d.c:896: warning: implicit declaration of function &#8216;glUseProgramObjectARB&#8217;
preview3d.c:897: warning: implicit declaration of function &#8216;glGetUniformLocationARB&#8217;
preview3d.c:898: warning: implicit declaration of function &#8216;glUniform1iARB&#8217;
preview3d.c:926: warning: implicit declaration of function &#8216;glUniform1fARB&#8217;
preview3d.c:946: warning: implicit declaration of function &#8216;glGenBuffersARB&#8217;
preview3d.c:946: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;vbo&#8217;
preview3d.c:947: warning: implicit declaration of function &#8216;glBindBufferARB&#8217;
preview3d.c:947: error: &#8216;GL_ARRAY_BUFFER_ARB&#8217; undeclared (first use in this function)
preview3d.c:947: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;vbo&#8217;
preview3d.c:948: warning: implicit declaration of function &#8216;glBufferDataARB&#8217;
preview3d.c:950: error: &#8216;GL_STATIC_DRAW_ARB&#8217; undeclared (first use in this function)
preview3d.c: In function &#8216;draw_object&#8217;:
preview3d.c:996: error: &#8216;GL_ARRAY_BUFFER_ARB&#8217; undeclared (first use in this function)
preview3d.c:996: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;vbo&#8217;
preview3d.c:1000: warning: implicit declaration of function &#8216;glVertexPointer&#8217;
preview3d.c:1000: error: &#8216;GL_FLOAT&#8217; undeclared (first use in this function)
preview3d.c:1001: warning: implicit declaration of function &#8216;glNormalPointer&#8217;
preview3d.c:1002: warning: implicit declaration of function &#8216;glClientActiveTexture&#8217;
preview3d.c:1002: error: &#8216;GL_TEXTURE4&#8217; undeclared (first use in this function)
preview3d.c:1003: warning: implicit declaration of function &#8216;glTexCoordPointer&#8217;
preview3d.c:1004: warning: implicit declaration of function &#8216;glEnableClientState&#8217;
preview3d.c:1004: error: &#8216;GL_TEXTURE_COORD_ARRAY&#8217; undeclared (first use in this function)
preview3d.c:1005: error: &#8216;GL_TEXTURE3&#8217; undeclared (first use in this function)
preview3d.c:1008: error: &#8216;GL_TEXTURE0&#8217; undeclared (first use in this function)
preview3d.c:1011: error: &#8216;GL_VERTEX_ARRAY&#8217; undeclared (first use in this function)
preview3d.c:1012: error: &#8216;GL_NORMAL_ARRAY&#8217; undeclared (first use in this function)
preview3d.c:1016: warning: implicit declaration of function &#8216;glDrawElements&#8217;
preview3d.c:1016: error: &#8216;GL_TRIANGLES&#8217; undeclared (first use in this function)
preview3d.c:1017: error: &#8216;GL_UNSIGNED_SHORT&#8217; undeclared (first use in this function)
preview3d.c:1019: warning: implicit declaration of function &#8216;glDisableClientState&#8217;
preview3d.c:1035: warning: implicit declaration of function &#8216;glBegin&#8217;
preview3d.c:1055: warning: implicit declaration of function &#8216;glColor3fv&#8217;
preview3d.c:1056: warning: implicit declaration of function &#8216;glNormal3fv&#8217;
preview3d.c:1057: warning: implicit declaration of function &#8216;glMultiTexCoord2fv&#8217;
preview3d.c:1058: error: &#8216;GL_TEXTURE1&#8217; undeclared (first use in this function)
preview3d.c:1060: error: &#8216;GL_TEXTURE2&#8217; undeclared (first use in this function)
preview3d.c:1061: warning: implicit declaration of function &#8216;glVertex3fv&#8217;
preview3d.c:1063: warning: implicit declaration of function &#8216;glEnd&#8217;
preview3d.c: In function &#8216;expose&#8217;:
preview3d.c:1075: error: &#8216;GLhandleARB&#8217; undeclared (first use in this function)
preview3d.c:1075: error: expected &#8216;;&#8217; before &#8216;prog&#8217;
preview3d.c:1082: warning: implicit declaration of function &#8216;glClear&#8217;
preview3d.c:1082: error: &#8216;GL_COLOR_BUFFER_BIT&#8217; undeclared (first use in this function)
preview3d.c:1082: error: &#8216;GL_DEPTH_BUFFER_BIT&#8217; undeclared (first use in this function)
preview3d.c:1091: warning: implicit declaration of function &#8216;glMatrixMode&#8217;
preview3d.c:1091: error: &#8216;GL_MODELVIEW&#8217; undeclared (first use in this function)
preview3d.c:1092: warning: implicit declaration of function &#8216;glLoadIdentity&#8217;
preview3d.c:1093: warning: implicit declaration of function &#8216;glRotatef&#8217;
preview3d.c:1096: warning: implicit declaration of function &#8216;glTranslatef&#8217;
preview3d.c:1101: warning: implicit declaration of function &#8216;glGetFloatv&#8217;
preview3d.c:1101: error: &#8216;GL_MODELVIEW_MATRIX&#8217; undeclared (first use in this function)
preview3d.c:1118: error: &#8216;prog&#8217; undeclared (first use in this function)
preview3d.c:1118: error: &#8216;programs&#8217; undeclared (first use in this function)
preview3d.c:1123: warning: implicit declaration of function &#8216;glUniform3fvARB&#8217;
preview3d.c:1133: warning: implicit declaration of function &#8216;glUniform2fvARB&#8217;
preview3d.c: In function &#8216;configure&#8217;:
preview3d.c:1164: warning: implicit declaration of function &#8216;glViewport&#8217;
preview3d.c:1166: error: &#8216;GL_PROJECTION&#8217; undeclared (first use in this function)
preview3d.c:1168: warning: implicit declaration of function &#8216;gluPerspective&#8217;
preview3d.c:1170: error: &#8216;GL_MODELVIEW&#8217; undeclared (first use in this function)
preview3d.c: In function &#8216;diffusemap_callback&#8217;:
preview3d.c:1302: error: &#8216;GLenum&#8217; undeclared (first use in this function)
preview3d.c:1302: error: expected &#8216;;&#8217; before &#8216;type&#8217;
preview3d.c:1308: error: &#8216;white_tex&#8217; undeclared (first use in this function)
preview3d.c:1310: error: &#8216;GL_TEXTURE1&#8217; undeclared (first use in this function)
preview3d.c:1311: error: &#8216;GL_TEXTURE_2D&#8217; undeclared (first use in this function)
preview3d.c:1325: error: &#8216;type&#8217; undeclared (first use in this function)
preview3d.c:1325: error: &#8216;GL_LUMINANCE&#8217; undeclared (first use in this function)
preview3d.c:1326: error: &#8216;GL_LUMINANCE_ALPHA&#8217; undeclared (first use in this function)
preview3d.c:1327: error: &#8216;GL_RGB&#8217; undeclared (first use in this function)
preview3d.c:1328: error: &#8216;GL_RGBA&#8217; undeclared (first use in this function)
preview3d.c:1337: warning: pointer targets in passing argument 3 of &#8216;get_nearest_pot&#8217; differ in signedness
preview3d.c:1337: warning: pointer targets in passing argument 4 of &#8216;get_nearest_pot&#8217; differ in signedness
preview3d.c:1347: error: &#8216;diffuse_tex&#8217; undeclared (first use in this function)
preview3d.c:1348: error: &#8216;GL_TEXTURE_WRAP_S&#8217; undeclared (first use in this function)
preview3d.c:1348: error: &#8216;GL_REPEAT&#8217; undeclared (first use in this function)
preview3d.c:1349: error: &#8216;GL_TEXTURE_WRAP_T&#8217; undeclared (first use in this function)
preview3d.c:1350: error: &#8216;GL_TEXTURE_MAG_FILTER&#8217; undeclared (first use in this function)
preview3d.c:1350: error: &#8216;GL_LINEAR&#8217; undeclared (first use in this function)
preview3d.c:1351: error: &#8216;GL_TEXTURE_MIN_FILTER&#8217; undeclared (first use in this function)
preview3d.c:1351: error: &#8216;GL_LINEAR_MIPMAP_LINEAR&#8217; undeclared (first use in this function)
preview3d.c:1353: warning: implicit declaration of function &#8216;glTexParameterfv&#8217;
preview3d.c:1353: error: &#8216;GL_TEXTURE_MAX_ANISOTROPY_EXT&#8217; undeclared (first use in this function)
preview3d.c:1355: error: &#8216;GL_GENERATE_MIPMAP_SGIS&#8217; undeclared (first use in this function)
preview3d.c:1355: error: &#8216;GL_TRUE&#8217; undeclared (first use in this function)
preview3d.c:1357: error: &#8216;GL_UNSIGNED_BYTE&#8217; undeclared (first use in this function)
preview3d.c: In function &#8216;glossmap_callback&#8217;:
preview3d.c:1392: error: &#8216;GLenum&#8217; undeclared (first use in this function)
preview3d.c:1392: error: expected &#8216;;&#8217; before &#8216;type&#8217;
preview3d.c:1399: error: &#8216;white_tex&#8217; undeclared (first use in this function)
preview3d.c:1401: error: &#8216;GL_TEXTURE2&#8217; undeclared (first use in this function)
preview3d.c:1402: error: &#8216;GL_TEXTURE_2D&#8217; undeclared (first use in this function)
preview3d.c:1416: error: &#8216;type&#8217; undeclared (first use in this function)
preview3d.c:1416: error: &#8216;GL_LUMINANCE&#8217; undeclared (first use in this function)
preview3d.c:1417: error: &#8216;GL_LUMINANCE_ALPHA&#8217; undeclared (first use in this function)
preview3d.c:1418: error: &#8216;GL_RGB&#8217; undeclared (first use in this function)
preview3d.c:1419: error: &#8216;GL_RGBA&#8217; undeclared (first use in this function)
preview3d.c:1428: warning: pointer targets in passing argument 3 of &#8216;get_nearest_pot&#8217; differ in signedness
preview3d.c:1428: warning: pointer targets in passing argument 4 of &#8216;get_nearest_pot&#8217; differ in signedness
preview3d.c:1438: error: &#8216;gloss_tex&#8217; undeclared (first use in this function)
preview3d.c:1439: error: &#8216;GL_TEXTURE_WRAP_S&#8217; undeclared (first use in this function)
preview3d.c:1439: error: &#8216;GL_REPEAT&#8217; undeclared (first use in this function)
preview3d.c:1440: error: &#8216;GL_TEXTURE_WRAP_T&#8217; undeclared (first use in this function)
preview3d.c:1441: error: &#8216;GL_TEXTURE_MAG_FILTER&#8217; undeclared (first use in this function)
preview3d.c:1441: error: &#8216;GL_LINEAR&#8217; undeclared (first use in this function)
preview3d.c:1442: error: &#8216;GL_TEXTURE_MIN_FILTER&#8217; undeclared (first use in this function)
preview3d.c:1442: error: &#8216;GL_LINEAR_MIPMAP_LINEAR&#8217; undeclared (first use in this function)
preview3d.c:1444: error: &#8216;GL_TEXTURE_MAX_ANISOTROPY_EXT&#8217; undeclared (first use in this function)
preview3d.c:1446: error: &#8216;GL_GENERATE_MIPMAP_SGIS&#8217; undeclared (first use in this function)
preview3d.c:1446: error: &#8216;GL_TRUE&#8217; undeclared (first use in this function)
preview3d.c:1448: error: &#8216;GL_UNSIGNED_BYTE&#8217; undeclared (first use in this function)
preview3d.c: In function &#8216;update_3D_preview&#8217;:
preview3d.c:1949: error: &#8216;GL_TEXTURE0&#8217; undeclared (first use in this function)
preview3d.c:1950: error: &#8216;GL_TEXTURE_2D&#8217; undeclared (first use in this function)
preview3d.c:1950: error: &#8216;normal_tex&#8217; undeclared (first use in this function)
preview3d.c:1951: error: &#8216;GL_TEXTURE_WRAP_S&#8217; undeclared (first use in this function)
preview3d.c:1951: error: &#8216;GL_REPEAT&#8217; undeclared (first use in this function)
preview3d.c:1952: error: &#8216;GL_TEXTURE_WRAP_T&#8217; undeclared (first use in this function)
preview3d.c:1953: error: &#8216;GL_TEXTURE_MAG_FILTER&#8217; undeclared (first use in this function)
preview3d.c:1953: error: &#8216;GL_LINEAR&#8217; undeclared (first use in this function)
preview3d.c:1954: error: &#8216;GL_TEXTURE_MIN_FILTER&#8217; undeclared (first use in this function)
preview3d.c:1954: error: &#8216;GL_LINEAR_MIPMAP_LINEAR&#8217; undeclared (first use in this function)
preview3d.c:1956: error: &#8216;GL_TEXTURE_MAX_ANISOTROPY_EXT&#8217; undeclared (first use in this function)
preview3d.c:1958: error: &#8216;GL_GENERATE_MIPMAP_SGIS&#8217; undeclared (first use in this function)
preview3d.c:1958: error: &#8216;GL_TRUE&#8217; undeclared (first use in this function)
preview3d.c:1960: error: &#8216;GL_RGBA&#8217; undeclared (first use in this function)
preview3d.c:1960: error: &#8216;GL_RGB&#8217; undeclared (first use in this function)
preview3d.c:1960: error: &#8216;GL_UNSIGNED_BYTE&#8217; undeclared (first use in this function)
make: *** [preview3d.o] Error 1

``` :(

**[edit2: i think i got it worked out all i need to figure out now is how can i get it to work.. :(]**

---

### Post by Megatog615 on 2007-09-14
Install the dev packages for GIMP and GLEW.

---

### Post by amixroed on 2007-09-14
have you tried installing Gimp 2.4 RC2 ? might work..

---

### Post by sammu on 2007-09-19
Problems with installing plugin here also. after typing make it tells me this:
Package gtkglext-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkglext-1.0.pc'
to the PKG_CONFIG_PATH environment variable

checked and it really was not there although i installed and reinstalled libgtkglext1 with synaptic.
So i tried to install gtkglext 1.2 source and ./configure ends up saying:
checking for X... no
configure: error: X development libraries not found

---

### Post by Megatog615 on 2007-09-21
Get the -dev packages for those.

---

### Post by fktt on 2007-09-26
i got it compiling, and it seemed to move the compiled plugin to the right folder too, but for some reason gimp just doesnt accept/cant find it for some reason.. :(

---

### Post by Megatog615 on 2007-09-26
It's under Filters -> Map.

---

### Post by fktt on 2007-09-27
> **Megatog615 said:**
> It's under Filters -> Map. nope, dont have it! :( weird..

---

### Post by Megatog615 on 2007-09-27
Did you run make install?

---

### Post by fktt on 2007-09-29
yes i did! well, doesnt matter, i guess.. havent had real extreem need for normal maps thus long and i can allways make em out of colormaps 'by hand' too, if i really need them.. :)

---

