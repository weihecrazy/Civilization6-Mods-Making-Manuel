以武刚车为例：
1. 定义一个新的单位需要以下几个文件：

2. Gameplay.xml
一个gameplay.xml文件里至少包括以下几个标签：
  <!--定义一个新的单位武刚车，他的类属于KIND_UNIT--> 
  <Types> 
    <Row Type="UNIT_WUGANCHE" Kind="KIND_UNIT" />
  </Types>
  <!--定义单位的AI类型，如战斗单位、探索者、近战、陆地战斗单位-->
  <UnitAiInfos>
    <Row UnitType="UNIT_WUGANCHE" AiType="UNITAI_COMBAT"/>
    <Row UnitType="UNIT_WUGANCHE" AiType="UNITAI_EXPLORE"/>
    <Row UnitType="UNIT_WUGANCHE" AiType="UNITTYPE_MELEE"/>
    <Row UnitType="UNIT_WUGANCHE" AiType="UNITTYPE_LAND_COMBAT"/>
  </UnitAiInfos>
  <!--定义单位类型为抗骑兵-->
  <TypeTags>
    <Row Type="UNIT_WUGANCHE" Tag="CLASS_ANTI_CAVALRY"/>
  </TypeTags>
  <!--定义单位的属性-->
  <Units>
    <Row UnitType="UNIT_WUGANCHE"
	 Cost="65"
	 Maintenance="1"
	 BaseMoves="2"
	 BaseSightRange="2"
	 ZoneOfControl="true"
	 Domain="DOMAIN_LAND"
	 Combat="25"
	 FormationClass="FORMATION_CLASS_LAND_COMBAT"
	 PromotionClass="PROMOTION_CLASS_ANTI_CAVALRY"
	 AdvisorType="ADVISOR_CONQUEST"
	 Name="LOC_UNIT_WUGANCHE_NAME"
	 Description="LOC_UNIT_WUGANCHE_DESCRIPTION"
	 PurchaseYield="YIELD_GOLD"
	 MandatoryObsoleteTech="TECH_METAL_CASTING"
	 PrereqTech="TECH_THE_WHEEL" />
		<!--如果是特色单位，则需要加上下面这句，"TRAIT_CIVILIZATION_UNIT_WUGANCHE"还需要在对应的领袖或者文明的xml中进行绑定-->
	 <!--TraitType="TRAIT_CIVILIZATION_UNIT_WUGANCHE"-->
  </Units>
  <!--定义升级后的单位-->
  <UnitUpgrades>
    <Row Unit="UNIT_WUGANCHE" UpgradeUnit="UNIT_PIKEMAN"/>
  </UnitUpgrades>
  <!--定义修改器-用于增加单位的特有属性或技能-->
  <TraitModifiers>
    <Row TraitType="TRAIT_CIVILIZATION_UNIT_WUGANCHE" ModifierId="WUGANCHE_NEIGHBOR_COMBAT"/>
  </TraitModifiers>


3. Icons.xml
这里采用了游戏原有的枪兵的图标
<?xml version="1.0" encoding="utf-8"?>
<GameData>
  <!-- For simplicity sake, we're going to reuse existing icons. -->
  <IconDefinitions>
    <!-- This is the unit icon for the unit. -->
    <Row Name="ICON_UNIT_WUGANCHE" Atlas="ICON_ATLAS_UNITS" Index="30"/>

    <!-- This is the portrait of the unit. -->
    <Row Name="ICON_UNIT_WUGANCHE_PORTRAIT" Atlas="ICON_ATLAS_UNIT_PORTRAITS" Index="28"/>

    <!-- Ethnic specific portrait of the unit.  This changes based on the leader. -->
    <Row Name="ICON_ETHNICITY_ASIAN_UNIT_WUGANCHE_PORTRAIT" Atlas="ICON_ATLAS_ASIAN_UNIT_PORTRAITS" Index="1"/>
    <Row Name="ICON_ETHNICITY_MEDIT_UNIT_WUGANCHE_PORTRAIT" Atlas="ICON_ATLAS_MEDITERRANEAN_UNIT_PORTRAITS" Index="1"/>
    <Row Name="ICON_ETHNICITY_SOUTHAM_UNIT_WUGANCHE_PORTRAIT" Atlas="ICON_ATLAS_SOUTH_AMERICAN_UNIT_PORTRAITS" Index="1"/>
    <Row Name="ICON_ETHNICITY_AFRICAN_UNIT_WUGANCHE_PORTRAIT" Atlas="ICON_ATLAS_AFRICAN_UNIT_PORTRAITS" Index="1"/>
  </IconDefinitions>
</GameData>

4. Text
<?xml version="1.0" encoding="utf-8"?>
<GameData>
  <LocalizedText>
    <!-- The name of the unit. -->
    <Row Tag="LOC_UNIT_WUGANCHE_NAME" Language="en_US">
      <Text>WUGANCHE</Text>
    </Row>

    <!-- It's description. -->
    <Row Tag="LOC_UNIT_WUGANCHE_DESCRIPTION" Language="en_US">
      <Text>Wugang is a kind of military vehicle in ancient China. It is a sharp weapon to prevent cavalry charge, and is used for land battles. +10 combat effectiveness when there is at least one adjacent wugang unit.</Text>
    </Row>

    <Row Tag="LOC_UNIT_WUGANCHE_NAME" Language="zh_Hans_CN">
      <Text>武刚车</Text>
    </Row>

    <!-- It's description. -->
    <Row Tag="LOC_UNIT_WUGANCHE_DESCRIPTION" Language="zh_Hans_CN">
      <Text>武刚车是中国古代的一种兵车，是防御骑兵冲锋的利器，用于陆上战斗。有至少一个相邻武刚车单位时，+10战斗力。</Text>
    </Row>
  </LocalizedText>
</GameData>
5. Units.Artdef
打开官方的Units.artdef文件，找到枪兵所在的element标签

复制element标签内的代码到自己的Units.artdef文件中，替换下面这部分的内容，然后将UNIT_PEON改为UNIT_WUGANCHE（你自己的单位名称）即可。这是利用了官方的枪兵模型。

6. Mod属性
在工程目录上右键，选择Properties

打开后如下，这里按照提示填写即可。

在in-game栏中加入4个新的动作，分别是updateDatabase、updateArt、updateIcons、updateText，然后分别将对应的文件添加到右边的框中。

7. build你的工程，现在一个新的单位mod就制作好了
