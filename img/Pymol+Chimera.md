### Pymol

***

 [第7章 蛋白质分子图形学.pptx](..\#########\我爱学习爱我\上课\7大三上\软件\分子生物学软件\PPT 分子生物学软件\第7章 蛋白质分子图形学.pptx) 

Some scripts (https://pymolwiki.org/index.php/Biochemistry_student_intro#Movie_of_1LEV)

#### Pymol软件的介绍 20201008 李鑫

***

* External GUI / Internal GUI
* ASHLC menu
  * **A** - *Actions*: Rename, duplicate, remove, apply presets (like "ball-and-stick" or "publication"), perform computations
  * **S** - *Show*: Change the way things appear, eg change to stick or cartoon view.
  * **H** - *Hide*: Things that are shown using **S** accumulate, and don't automatically replace the last view. **H** is the opposite of **S** and hides unwanted representations.
  * **L** - *Label*: Label atoms, residues, etc.
  * **C** - *Color*: Change the color of atoms and groups.
* 显示蛋白质氨基酸序列：Internal GUI 右下角S (PDB: 4N1Z)![image-20201008092400027](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008092400027.png)
* 选取多聚体中的某一链 ：External GUI - Display - Sequence mode - chain identifiers 
* 改变cartoon 显示形式 ： setting - cartoon - cylindrical helices（圆柱体）![image-20201008092245746](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008092245746.png)
* 改变cartoon颜色 - Internal - color - spectrum - rainbow
* 无法撤销undo ：File - save session as - **每步保存**
* 换背景 - Display - Background - white![image-20201008093329486](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008093329486.png)
* command line "z" = zoom 视野回到中间
* 调整透明度 - Setting - transparency - cartoon - 60% ![image-20201008093753709](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008093753709.png)

* 输出高分辨率图片 with command line ("ray 1200, 1000") （1200 1000指分辨率）
* File - save image as (capture current display)![01](C:\Users\lenovo\Desktop\01.png)
* 设置长宽480 600 背景为白色![02](C:\Users\lenovo\Desktop\02.png)

* 显示ligand - protein 相互作用 ：Internal - 选中ligand - A - find - polar contacts - with other atoms![image-20201008101453048](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008101453048.png)
* 修改显示大小： External - Setting - Edit all - sphere_scale (from 1 to 0.5) （这里显示修改球的大小）
* label name ： 右键点击原子 - label - label atom name （无效）
* 单击右下角 viewing 变成 editing
  * ctrl + 鼠标左键 可以任意拖拽 （可以拖拽 label name 也可以修改键长键角 修改原子位置）
* 只显示与配体相互作用的氨基酸侧链 需要先选中看到相互作用的几个atom
  * Internal - A - extract object - get object 01
  * 隐藏其他不相关的sticks，将object叠加回原本的大结构中
  * ![image-20201008110146428](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008110146428.png)

***

##### Example 2  看单体是否有可能成为多聚体

***

PDB: 3RBM ![image-20201008103414584](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008103414584.png)

* select and remove B,C,D （command line "remove sel"）

* A - generate - symmetry mates - within X A
  * show出各种对称的单体 可以看到是否能形成多聚体

* 导入和看电子云密度
  * 查询电子云密度 https://eds.bmc.uu.se/eds/
  * ![image-20201008105001202](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008105001202.png)
  * maps - 下载CCP4格式
  * ![image-20201008105030378](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008105030378.png)
  * 修改下载下来的.ccp4文件的名字 防止pymol直接定义为一个文件 会重复 
  * 电子云密度文件 internal - A - mesh - 0 level 1.0
  * ![image-20201008110021464](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008110021464.png)
  * 看ligand是否被电子云密度包裹得较好，主要看灵活的烷基链末端是否能够较好地包裹在电子云密度中

***

##### example 3 氨基酸叠合比对

打开4n1z 和3rbm

* Internal - A - align - to molecule 进行氨基酸叠合比对![image-20201008111153318](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008111153318.png)
* External - Wizard - Measurement - click first - click second ： 显示X A 的距离
* 不测了就点done
* ![image-20201008111607328](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008111607328.png)
* ![image-20201008111323843](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20201008111323843.png)
* 鼠标左键点击切换residues to atoms  可以选取特定的atom而不是residue

#### 做movie 结构动画

***

* movie - program - camera loop - x-roll - 8 seconds ： x轴旋转8s
* purge movie 去掉刚刚的movie
* 场景转换制作movie
  * Scene - store F1,F2,F3（F1,2,3 分别是三个不同的视角/场景 自己设置）
  * movie - program - scene loop - nutate 停顿
  * 我保存的前两段是失败的sweep movie 后边是以每帧转30度的动画

* 导出： file - save movie as

* 输入 command line "**center**" 可居中



***

**注意**：

* 保存的session如果路径中有中文，会无法打开，如果需要再重新打开就把它重新拉到桌面上再打开
* [pymolwiki](https://pymolwiki.org/index.php/Main_Page) to find more help and tutorial
* Schrodinger软件负责计算分析
* Pymol负责作图

### Chimera

***

`open` read local files or fetch by ID (e.g. PDB ID)

`focus` adjust the view and center of rotation

`color` color red :lys

`match` superimpose 2 models by a least-squares fit of specified atoms

`rlabel` display residue labels 

`sel` select (e.g. select :.a to select chain A)

`help` help command

`~rlabel` `~rdisp` `~ribbon` to remove label/disp/ribbon imposed before

`close 0` remove the model

`stop` exit from Chimera

| Atom Specification Symbols |                            |                                                              |
| -------------------------- | -------------------------- | ------------------------------------------------------------ |
| Symbol                     | Meaning                    | Usage                                                        |
| **#**                      | model                      | #*model* (model ID number)                                   |
| **:**                      | residue                    | :*residue* (residue name or number)                          |
| **:.**                     | chain                      | :.*chain* (chain ID)                                         |
| **@**                      | atom                       | @*atom* (atom name)                                          |
| **=**                      | partial wildcard           | matches partial atom or residue name, *e.g.*, **@C=** specifies all atoms with names beginning with C |
| **?**                      | single-character  wildcard | matches single character in atom or residue name, *e.g.*, **:G??**specifies all residues with three-letter names beginning with G |



选取结构进行分析

RdRp

| PDB code | Structure depiction                                          | Resolution | Paper               | Journal         | Method |
| -------- | ------------------------------------------------------------ | ---------- | ------------------- | --------------- | ------ |
| 7BV1     | apo nsp12-nsp7-nsp8 complex                                  | 2.80       | Yin et al. June     | Science         | EM     |
| 7C2K     | Nsp12-nsp7-nsp8-RNA **pre**-translocated catalytic complex structure | 2.93       | Wang et al. July    | Cell            | EM     |
| 7BZF     | Nsp12-nsp7-nsp8-RNA **post**-translocated catalytic complex structure | 3.26       | Wang et al. July    | Cell            | EM     |
| 6YYT     | replicating SARS-CoV-2 polymerase                            | 2.90       | Hilen et al. August | Nature          | EM     |
| 6M71     | RNA-dependent RNA polymerase in complex with cofactors       | 2.90       | Gao et al. May      | Science         | EM     |
| 6XEZ     | SARS-CoV-2 replication-transcription complex bound to nsp13 helicase -nsp13-RTC (CHAPSO) | 3.50       | Chen et al. July    | BioRxiv         | EM     |
| 6XQB     | SARS-CoV-2 RdRp/RNA complex                                  | 3.40       | TBP                 | to be published | EM     |

描述并总结蛋白质分子中氨基酸的空间分布特点

结合该蛋白质分子的性质与生物学功能对某个种类或某个氨基酸在蛋白质分子的结构及功能中发挥的作用机制进行分析

如果将氨基酸突变成为其它氨基酸，将可能对蛋白质的结构与功能产生什么影响。

