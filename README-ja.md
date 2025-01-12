# UmaMusumeMME
MMD用ウマ娘シェーダー

Model rip by 红白de黑白、无名

![shader](https://github.com/croakfang/UmaMusumeMME/assets/32562737/508479a2-44d5-4fbf-9633-a4835d6a7d5b)

# 使い方
このMMEを完全に動作させるには、[UmaViewer](https://github.com/katboi01/UmaViewer)を使用してエクスポートされたモデルが必要です。 

### `UMA_Body.fx` / `UMA_Hair.fx` / `UMA_Tail.fx` について
1. 以下の内容を見つけてください。：
```
texture TripleMaskTexture < string ResourceName = "Texture2D/tex_bdy2005_00_base.png"; > ;
texture OptionMaskTexture < string ResourceName = "Texture2D/tex_bdy2005_00_ctrl.png"; > ;
texture ToonMapTexture < string ResourceName = "Texture2D/tex_bdy2005_00_shad_c.png"; > ;
texture EnvMapTexture < string ResourceName = "Texture2D/tex_chr_env000.png"; > ;
```  
2. `ResourceName`を、レンダリングしたいウマ娘の該当する部位のテクスチャに変更します。変更部分は主に番号で、`base`/`ctrl`/`shad_c`といった接尾辞は変更しないでください。

### `UMA_Eye.fx` / `UMA_Face.fx`について
1. 以下の内容を見つけてください。：
```
texture TripleMaskTexture < string ResourceName = "Texture2D/tex_bdy2005_00_base.png"; > ;
texture OptionMaskTexture < string ResourceName = "Texture2D/tex_bdy2005_00_ctrl.png"; > ;
texture ToonMapTexture < string ResourceName = "Texture2D/tex_bdy2005_00_shad_c.png"; > ;
texture EnvMapTexture < string ResourceName = "Texture2D/tex_chr_env000.png"; > ;

texture MainTex < string ResourceName = "Texture2D/tex_chr2005_00_eye0_all.png"; > ;
texture High0Tex < string ResourceName = "Texture2D/tex_chr2005_00_eyehi00.png"; > ;
texture High1Tex < string ResourceName = "Texture2D/tex_chr2005_00_eyehi01.png"; > ;
texture High2Tex < string ResourceName = "Texture2D/tex_chr2005_00_eyehi02.png"; > ;
```
2. `ResourceName`を、レンダリングしたいウマ娘の該当する部位のテクスチャに変更します。
3. モデル名を英語に変更します。（例：Daitaku Helios.pmx）
4. モデルにボーン頭部（`head`）を追加し、その親ボーンを「`頭`」として位置を一致させます。
5. 以下のパラメータを見つけてください。  
   ```
   float4x4 _faceShadowHeadMat : CONTROLOBJECT < string name = "model.pmx"; string item = "摢"; >
   ```  
   `name`にモデル名を置き換え、`item`を`head`に置き換えます。
   （例：  
   ```
   float4x4 _faceShadowHeadMat : CONTROLOBJECT < string name = "model.pmx"; string item = "head"; >
   ```
### 重要なパラメータ
その他の値は変更しないことをお勧めします。 
|パラメータ名|説明|
|-|-|
|_ToonStep|陰影の範囲|
|_ToonFeather|陰影のぼかし|
|_ToonBrightColor|明るい部分の色|
|_ToonBrightColor|暗い部分の色（陰影）|
|_RimStep|縁光の範囲|
|_RimFeather|縁光のぼかし|
|_RimColor|緑光の色|
|_OutlineWidth|描線の太さ|
|_OutlineColor|描線の色|
|_GlobalOutlineOffset|描線のZオフセット（値は0以下である必要あり）。黒いブロックが表示される場合、この値を徐々に減らして調整してください。|

