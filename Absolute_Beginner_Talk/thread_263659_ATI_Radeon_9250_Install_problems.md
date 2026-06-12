---
title: "ATI Radeon 9250 Install problems"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-09-23
Ok, I have done what it says here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

> 
 Installing the driver

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

Help on enabling repositories can be found at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Now Reboot your system:

sudo shutdown -r now

But when i reboot and do:
fglrxinfo
I get all these errors!:
```

^[[Ajosh@joshlinux:~$ fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
josh@joshlinux:~$

```

Any ideas? Im using Radeon 9250 128meg AGP card. :)

edit:
Also, the screen size is 1280x something now.. and its hard to read since im use to 1024x whatever it normally is :P

---

### Post by petri on 2006-09-23
Just continue the howto for **Troubleshooting for Method 1**

> Unfortunately OpenGL seems to be broken for R200 cards (everything below Radeon 9500) in this driver version which results in messages like 

    [fglrx] API ERROR: could not register entrypoint for Uniform2iARB

---

### Post by Josh1 on 2006-09-23
> **petri said:**
> Just continue the howto for **Troubleshooting for Method 1**

I did, but that didn't fix it either. I'm now doing "sudo dpkg-reconfigure xserver-xorg" :).

---

### Post by powder on 2006-09-23
I hope you're not trying to install the latest fglrx drivers (8.29.6) as ATI has removed R200 support officially.

---

### Post by Josh1 on 2006-09-23
> **powder said:**
> I hope you're not trying to install the latest fglrx drivers (8.29.6) as ATI has removed R200 support officially.

I just did as that said, lol.
Now when I do fglxinfo I get:
```

josh@joshlinux:~$ fglrxinfo display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by petri on 2006-09-23
> **powder said:**
> I hope you're not trying to install the latest fglrx drivers (8.29.6) as ATI has removed R200 support officially.


When they did do that? :eek:

---

### Post by petri on 2006-09-23
> **Josh1 said:**
> I just did as that said, lol.

Try to find older drivers :-s  and then it should work.

---

### Post by powder on 2006-09-23
> **petri said:**
> When they did do that? :eek:

R200 support has been broken for some time now.  ATI don't want to fix it so they dropped support officially.  It's probably the best decision because they can focus on other things than fixing broken R200 support.

If you do have an R200, I recommend you use Method 1 and install xorg-driver-fglrx.  There is a workaround in the troubleshooting section for R200 based cards.

---

### Post by petri on 2006-09-23
Mine did not work with method 1 but it does work with method 2 :)

---

