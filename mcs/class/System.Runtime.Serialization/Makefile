thisdir = class/System.Runtime.Serialization
SUBDIRS = 
include ../../build/rules.make

RESOURCE_FILES = \
	resources/mstypes.schema

LIBRARY = System.Runtime.Serialization.dll
LIB_MCS_FLAGS = \
			/nowarn:168,169,219,414 \
	        /r:System.dll \
	        /r:System.Xml.dll \
		/r:System.Core.dll \
	        $(RESOURCE_FILES:%=/resource:%)

ifneq (2.1, $(FRAMEWORK_VERSION))
LIB_MCS_FLAGS += /d:NET_3_0 /r:System.Data.dll /r:System.Configuration.dll
endif

ifeq (unity, $(PROFILE))
LIB_MCS_FLAGS += -d:UNITY_3_0
endif

TEST_MCS_FLAGS = $(LIB_MCS_FLAGS) /r:System.ServiceModel.dll

EXTRA_DISTFILES = $(RESOURCE_FILES) \
	Test/Resources/FrameworkTypes/* \
	Test/Resources/Schemas/*.xsd \
	Test/System.Runtime.Serialization/one.xml

VALID_PROFILE := $(filter 2.0 2.1 4.0, $(FRAMEWORK_VERSION))
ifndef VALID_PROFILE
LIBRARY_NAME = dummy-System.Runtime.Serialization.dll
NO_INSTALL = yes
NO_SIGN_ASSEMBLY = yes
NO_TEST = yes
endif

include ../../build/library.make
