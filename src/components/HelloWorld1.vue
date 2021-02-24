<template>
    <div class="form">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" labelPosition='top' label-width="100px" class="demo-ruleForm">
            <el-form-item label="填表时间" required>
                <el-date-picker v-model="ruleForm.addtime" type="date" placeholder="选择日期"> </el-date-picker>
            </el-form-item>
            <el-form-item label="机构名称" prop="region">
                <el-input v-model="ruleForm.username"></el-input>
            </el-form-item>
            <el-form-item label="法人姓名" prop="region">
                <p>后附个人简历</p>
                <el-input v-model="ruleForm.username"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="法人手机" prop="region">
                <el-input v-model="ruleForm.corporatePhone"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="法人办公电话" prop="region">
                <el-input v-model="ruleForm.officeTelephone"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="机构联系人" prop="region">
                <el-input v-model="ruleForm.institutionalContact"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="机构联系人手机" prop="region">
                <el-input v-model="ruleForm.institutionalContactMobile"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="机构联系人办公电话" prop="region">
                <el-input v-model="ruleForm.institutionalContactOfficeTelephone"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="办公地址" prop="region">
                <p>后附办公场地介绍</p>
                <el-input v-model="ruleForm.officeAddress"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="上传营业执照或登记证" required>
                <el-upload class="avatar-uploader" action="https://jsonplaceholder.typicode.com/posts/" :show-file-list="false" :on-success="handleAvatarSuccess" :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                </el-upload>
            </el-form-item>
            <!--  -->
            <el-form-item label="组织机构代码" prop="region">
                <el-input v-model="ruleForm.OrganizationCode"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="登记类型" prop="region">
                <el-input v-model="ruleForm.registrationType"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="电子邮箱" prop="region">
                <el-input v-model="ruleForm.email"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="成立时间" required>
                <el-date-picker v-model="ruleForm.timeOfEstablishment" type="date" placeholder="选择日期"> </el-date-picker>
            </el-form-item>
            <!--  -->
            <el-form-item label="推荐人(推荐理由)" prop="region">
                <el-input v-model="ruleForm.references"></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="是否成立党组织" required>
                <el-radio-group v-model="ruleForm.partyOrganization">
                    <el-radio label="是"></el-radio>
                    <el-radio label="否"></el-radio>
                </el-radio-group>
            </el-form-item>
            <!--  -->
            <el-form-item label="机构简介" prop="region">
                <p>包括本机构人员构成、办公场地面积、服务设施和服务项目、党建开展情况以及加入联合会单位会员的工作计划和合作设想等，不少于400字。</p>
                <el-input v-model="ruleForm.organizationProfile" type='textarea'></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="单位会员申请书" prop="region">
                <p>包括本机构在行业领域取得的成就，未来3-5年的发展目标和规划，作为单位会员能提供的资源优势和合作领域，是否接受过相关培训等，不少于300字。</p>
                <el-input v-model="ruleForm.unitApplication" type='textarea'></el-input>
            </el-form-item>
            <!--  -->
            <el-form-item label="法人简历" prop="region">
                <p>个人履历</p>
                <el-input v-model="ruleForm.personalResume"></el-input>
            </el-form-item>
            <!-- idcard -->
            <el-form-item label="上传法人身份证件图片" required>
                <el-upload class="avatar-uploader" action="https://jsonplaceholder.typicode.com/posts/" :show-file-list="false" :on-success="handleAvatarSuccess" :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                </el-upload>
            </el-form-item>
            <!-- Diploma -->
            <el-form-item label="上传法人学历/职称/资质证书图片" required>
                <el-upload class="avatar-uploader" action="https://jsonplaceholder.typicode.com/posts/" :show-file-list="false" :on-success="handleAvatarSuccess" :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
                </el-upload>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('ruleForm')">立即创建</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    export default {
        name: 'form',
        data() {
            return {
                ruleForm: {
                    addtime: '', // 填表时间
                    username: '', // 姓名
                    gender: '', // 性别
                    birthday: '', // 生日
                    culture: '', // 文化程度
                    politicalOutlook: '', // 政治面貌
                    vocationalQualifications: '', // 职业资质
                    idCard: '', // 身份证号
                    mobile: '', // 手机号
                    address: '', // 通讯地址
                    application: '', // 会员申请书
                    delivery: false,
                    type: [],
                    resource: '',
                    desc: '',
                    corporatePhone: '', // 法人手机
                    officeTelephone: '', // 法人办公电话
                    institutionalContact: '', // 机构联系人
                    institutionalContactMobile: '', // 机构联系人手机
                    institutionalContactOfficeTelephone: '', // 机构联系人办公电话
                    officeAddress: '', // 办公地址
                    OrganizationCode: '', // 组织机构代码
                    registrationType: '', // 登记类型
                    email: '', // 邮箱
                    timeOfEstablishment: '', // 成立时间
                    references: '', // 推荐人(推荐理由)
                    partyOrganization: '', // 是否成立党组织
                    organizationProfile: '', // 机构简介
                    unitApplication: '', // 单位会员申请书
                    personalResume: '', // 法人建立
                },
                imageUrl: '',
                fileList: [], //附件
                uploadUrl: 'https://jsonplaceholder.typicode.com/posts/',
                rules: {
                    region: [{
                        required: true,
                        message: '请选择活动区域',
                        trigger: 'change'
                    }],
                    date1: [{
                        type: 'date',
                        required: true,
                        message: '请选择日期',
                        trigger: 'change'
                    }],
                    date2: [{
                        type: 'date',
                        required: true,
                        message: '请选择时间',
                        trigger: 'change'
                    }],
                    type: [{
                        type: 'array',
                        required: true,
                        message: '请至少选择一个活动性质',
                        trigger: 'change'
                    }],
                    resource: [{
                        required: true,
                        message: '请选择活动资源',
                        trigger: 'change'
                    }],
                    desc: [{
                        required: true,
                        message: '请填写活动形式',
                        trigger: 'blur'
                    }]
                }
            }
        },
        methods: {
            submitForm(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            handleAvatarSuccess(res, file) {
                this.imageUrl = URL.createObjectURL(file.raw);
            },
            beforeAvatarUpload(file) {
                const isJPG = file.type === 'image/jpeg';
                const isLt2M = file.size / 1024 / 1024 < 2;
                if (!isJPG) {
                    this.$message.error('上传头像图片只能是 JPG 格式!');
                }
                if (!isLt2M) {
                    this.$message.error('上传头像图片大小不能超过 2MB!');
                }
                return isJPG && isLt2M;
            }
        }
    }
</script>

<style scoped>
    .form {
        max-width: 600px;
        margin: 0 auto;
    }
    .form p {
        font-size: 14px;
        margin-top: 0;
        margin-bottom: 10px;
        line-height: 20px;
        color: #999;
    }
    .avatar-uploader .el-upload {
        border: 1px dashed #d9d9d9;
        border-radius: 6px;
        cursor: pointer;
        position: relative;
        overflow: hidden;
    }
    .avatar-uploader .el-upload:hover {
        border-color: #409EFF;
    }
    .avatar-uploader-icon {
        font-size: 28px;
        color: #8c939d;
        width: 178px;
        height: 178px;
        line-height: 178px;
        text-align: center;
    }
    .avatar {
        width: 178px;
        height: 178px;
        display: block;
    }
</style>
